.. _ref-compilers:

=========
Compilers
=========


Coffee Script compiler
======================

The Coffee Script compiler use `Coffee Script <http://jashkenas.github.com/coffee-script/>`_
to compile your javascripts.

To use it add this to your ``COMPRESS_COMPILERS`` ::

  COMPRESS_COMPILERS = (
    'compress.compilers.coffee.CoffeeScriptCompiler',
  )

``COMPRESS_COFFEE_SCRIPT_BINARY``
---------------------------------

  Command line to execute for coffee program.
  You will most likely change this to the location of coffee on your system.

  Defaults to ``'/usr/local/bin/coffee'``.

``COMPRESS_COFFEE_SCRIPT_ARGUMENTS``
------------------------------------
  
  Additional arguments to use when coffee is called.
  
  Defaults to ``''``.

LESS compiler
=============

The LESS compiler use `LESS <http://lesscss.org/>`_
to compile your stylesheets.

To use it add this to your ``COMPRESS_COMPILERS`` ::

  COMPRESS_COMPILERS = (
    'compress.compilers.less.LessCompiler',
  )

``COMPRESS_LESS_BINARY``
------------------------

  Command line to execute for lessc program.
  You will most likely change this to the location of lessc on your system.

  Defaults to ``'/usr/local/bin/lessc'``.

``COMPRESS_LESS_ARGUMENTS``
---------------------------

  Additional arguments to use when lessc is called.

  Defaults to ``''``.

SASS compiler
=============

The SASS compiler use `SASS <http://sass-lang.com/>`_
to compile your stylesheets.

To use it add this to your ``COMPRESS_COMPILERS`` ::

  COMPRESS_COMPILERS = (
    'compress.compilers.sass.SASSCompiler',
  )


``COMPRESS_SASS_BINARY``
------------------------
  
  Command line to execute for sass program.
  You will most likely change this to the location of sass on your system.

  Defaults to ``'/usr/local/bin/sass'``.

``COMPRESS_SASS_ARGUMENTS``
---------------------------
  
  Additional arguments to use when sass is called.

  Defaults to ``''``.


Write your own compiler class
=============================

To write your own compiler class, for example want to implement other types
of compilers.

All you need to do is to create a class that inherits from ``compress.compilers.CompilerBase``
and implements ``match_file`` and ``compile_file`` when needed.

Finally, specify it in the tuple of compilers ``COMPRESS_COMPILERS`` in the settings.

Example
-------

A custom compiler for a imaginary compiler called jam ::

  from compress.compilers import CompilerBase
  
  class JamCompiler(CompilerBase):
    output_extension = 'js'
    
    def match_file(self, filename):
      return path.endswith('.jam')
    
    def compile_file(self, content):
      return jam.compile(content)
