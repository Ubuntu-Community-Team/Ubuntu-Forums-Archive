---
title: "How do I install koffice-2.22.2 in Ubuntu 10.04?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by xmanx on 2010-09-12
Hi to all here.
I'm new to Ubuntu.
I'd like to install koffice-2.2.2 tar.bz2 in ubuntu 10.04.
I have a folder readme-packagers
Packaging Information for KOffice.
----------------------------------

We recommend building several binary packages from the KOffice source.

Splitting KOffice into packages:
 * gives users a better choice of which components they have
   installed;
 * allows users to install just the applications without unnecessary
   dependencies;
 * helps to reduce packaging conflicts for users with non-standard
   package selections.


Table Of Contents
-----------------
1. Kexi
1.1. Kexi database and migration drivers
1.2. Kexi default database driver: SQLite
1.3. Kexi development files
1.4. Quick command-line tests of Kexi installation
2. Krita
2.1. Krita development files
3. Debug information
4. KOffice libraries

1. Kexi
=======

1.1. Kexi database and migration drivers
----------------------------------------

Kexi provides database drivers and migration drivers for a number of
database types or data sources. The following matrix lists them:

 Name         Database driver files            Migration driver files
 ------------------------------------------------------------------------
 MySQL        kexidb_mysqldriver.so            keximigrate_mysql.so
              kexidb_mysqldriver.desktop       keximigrate_mysql.desktop
 PostgreSQL   kexidb_pqxxsqldriver.so          keximigrate_pqxx.so
              kexidb_pqxxsqldriver.desktop     keximigrate_pqxx.desktop
 Sybase & MS SQL Server
              kexidb_sybasedriver.so           keximigrate_sybase.so
              kexidb_sybasedriver.desktop      keximigrate_sybase.desktop
 XBase
              kexidb_xbasedriver.so            keximigrate_xbase.so
              kexidb_xbasedriver.desktop       keximigrate_xbase.desktop

(Oracle driver is not currently distributed)

Plugin .so files typically go to $KDEDIR/lib/kde4,
and .desktop service files go to $KDEDIR/share/services/.

We suggest putting each driver in a separate package, and that installation of
these packages be optional.  Each driver package may then depend on the corresponding
'native' libraries. For example libmysqlclient for MySQL and libpqxx for PostgreSQL
(libpqxx in turn depends on libpq).

TODO: add dependencies to the table above and minimal versions of them

1.2. Kexi default database driver: SQLite
-----------------------------------------

In contrast to the other database drivers, SQLite 3 driver should be part
of the main Kexi package. Thus, Kexi main package should depend on SQLite 3 package.

TODO: explain minimal SQLite version, and its features ([http://kdedevelopers.org/node/4156](http://kdedevelopers.org/node/4156))


1.3. Kexi development files
---------------------------

Kexi ships no development files at the moment, so -devel packages are not needed.


1.4. Quick command-line tests of Kexi installation
--------------------------------------------------

If you don't want to click through Kexi interface but still want
to make (almost) sure the application is properly packaged, please 
install it and type the following from the command line:

 kexi --create-opendb --drv sqlite3 --new form testdb

(ignore possible warning messages)
This will:
- create a new empty database file "testdb",
- open it,
- create a new empty form


2. Krita
========

2.1. Krita development files
----------------------------

Location: koffice/krita/image, koffice/krita/ui

These directories contain header files that are installed and can be
used by plugin developers to extend Krita with new tools, colorspaces,
paint-ops and more.  If your distribution packages development files
separately, it may be a good idea to make a package with these headers.


3. Debug information
====================

For alpha and beta packages, please build with debug output enabled, but for
production packages the -DCMAKE_CXX_FLAGS="-DKDE_NO_DEBUG_OUTPUT" is recommended.
A significant performance increase will be the result.


4. KOffice libraries
====================

KOffice share common functionality within libraries, placed in libs/ subdirectory.
KOffice libraries should be placed in a single package, separate from KOffice applications.
Below is the list of the libraries.

Name       Conditional compilation flag    Globally used in KOffice?   Public API
                                                                       (headers installed)
           (default: NO)                   (default: YES)              (default: YES)
------------------------------------------------------------------------------------------

flake
kokross    SHOULD_BUILD_SCRIPTING                                      NO
kopageapp
koplugin                                                               NO
koproperty                                 Kexi, KPlato                NO
koreports                                  Kexi, KPlato                NO
kotext
main
odf
pigment
widgets

Readme--------------

Office is a collection of office applications linked together by a
common base.  This common base assures that all office application can
work together and also share a common look and feel.


KOffice is free software, mostly under LGPL 2+ but also under the GPL.
See COPYING and COPYING.LIB for the details.  See also copyright and
licensing notices in individual files.


Contents
--------

The applications currently included in KOffice (version 2.1) are:

Office productivity:
- KWord      -  Word processor
- KSpread    -  Spreadsheet calculator
- KPresenter -  Presentation program

Graphics:
- Karbon     -  Vector graphics 
- Krita      -  Advanced drawing and image manipulation

More information about Krita can be found at [http://www.krita.org](http://www.krita.org)

Management:
- KPlato     -  Project planning
- Kexi       -  Integrated data management

Advanced plugins:
- KChart     -  Graphic data visualization
- KFormula   -  Mathematical formulas

The applications not yet part of the official release, but will
be included in a next version:

- Kivio      -  Flowcharting program

More information can be found at [http://www.koffice.org](http://www.koffice.org)


Building and running
--------------------

KOffice is based on the KDE libraries ( [http://www.kde.org](http://www.kde.org) ) which are
needed to run KOffice.  Note that you don't have to actually run the
KDE desktop environment in order to use KOffice.  KOffice works fine
on any desktop or platform.

You will need kdesupport, kdelibs and kdebase/runtime
installed if you want to compile and run KOffice. Installing kdepimlibs
gives more functionality.
For importing some external file formats or other plugins, you may
also need some other dependencies.  For more details on how to build
KOffice from the sources, see
[http://wiki.koffice.org/index.php?title=Build_KOffice](http://wiki.koffice.org/index.php?title=Build_KOffice)


Developers
----------

KOffice is created by the KDE community, consisting of Open Source
programmers around the world.  All developers give their time/code to
the community for everyone to benefit.

If you have found a bug or missing feature you can always contact the
developers of KOffice (via [http://www.koffice.org](http://www.koffice.org)) or delve into the
source code yourself.

The parts that are shared between all KOffice applications can be found
in the libs/ subdirectory.  There classes like KoDocument can be found;
these classes are extended in the project directories.

Read the .h files in the respective directories for more info or read
the online API docs which you can find at
[http://www.koffice.org/developer/apidocmain.php](http://www.koffice.org/developer/apidocmain.php)


The KOffice source tree
-----------------------

Here follows a short overview of the source code.

cmake/       files to help cmake do it's job configuring
doc/         user documentation.  

karbon/      source code of the different applications
kexi/
kplato/
kpresenter/  
krita/
kspread/
kword/
kivio/

kchart/      source code of two applications who are now available as shapes.
kformula/

kounavail    a shape that is used when an application that handles a
             certain embedded datatype is not available

libs/        the common libraries
plugins/     some plugins, both flake shapes and other types.

filters/     import and export filters for foreign file formats

tools/       tools used internally (e.g. for testing) and released
             with koffice, such as the koconverter file format 
             conversion tool.

interfaces/  simplified external interfaces to some advanced data types
             such as charts.

servicetypes/ desktop files for some service types provided by KOffice

templates/   templates for new documents.
             NOTE: Out of date since they use the old KOffice file formats

kdgantt/     and advanced gantt chart library provided by an external vendor.

pics/        icons


Contact info
------------

User mailing list:      mailto:koffice@kde.org
Developer mailing list: mailto:koffice-devel@kde.org
Krita mailing list:     mailto:kimag*****@kde.org

Subscribing and list information: [http://www.kde.org/mailinglists](http://www.kde.org/mailinglists)
Archives: [http://lists.kde.org](http://lists.kde.org)

IRC channel for developers:  #koffice on irc.freenode.org
IRC channel for Krita: #krita on irc.freenode.org

KOffice forums:         [http://forum.kde.org/viewforum.php?f=96](http://forum.kde.org/viewforum.php?f=96)
Krita forums:           [http://forum.kde.org/viewforum.php?f=136](http://forum.kde.org/viewforum.php?f=136)

If you have questions about this README file or about KOffice in general,
please mail to the KOffice mailing list: mailto:koffice@kde.org


Thomas Zander
Chris Lee
Inge Wallin
Boudewijn Rempt

---

### Post by LowSky on 2010-09-13
Ubuntu had koffice 2.1.2 in the repos if if you wish to use that

sudo apt-get install koffice

Note it will install a good deal of KDE packages just to  get it running

---

