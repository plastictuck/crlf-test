Git to the end of the line
==========================

About Git diff
--------------

When running Git commands like ``git diff``, you sometimes see some ``^M``
characters which represent the ``CR`` part of DOS ``CRLF`` line endings.  Unix
line endings use only ``LF`` and Git was written with this in mind.  Currently,
most operating systems use Unix line endings (Linux, Android, Mac OSX,
Solaris...)  but MS Windows still uses the MS-DOS line endings.

To hide the ``^M`` characters and avoid messy patches created with ``git
diff``, run the following command inside your copy of a Git repository
containing files with DOS line endings::

  git config core.whitespace cr-at-eol

If you want to enable this on all your repositories, typically if you use Git
on Windows, add the ``--global`` option so you don't need to do it again in
each repository::

  git config --global core.whitespace cr-at-eol

Keeping it sane
---------------

Another important feature of Git is the ability to automatically replace the
line endings to a specific type at commit time to avoid inconsistencies within
a file.  For example, if you use DOS line endings ``CRLF`` and want to ensure
that users editing the files with Unix-like operating systems don't add lines
with only ``LF``, you can create a ``.gitattributes`` file at the top of your
repository with the following contents::

  * text eol=crlf

To read more about the subject, see `Dealing with line endings
<https://help.github.com/articles/dealing-with-line-endings>`_.
