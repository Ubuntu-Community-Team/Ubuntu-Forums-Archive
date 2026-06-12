---
title: "Where do I find installed packeges to delete them manually?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Ubunser on 2010-02-01
When I install them where does system place them? I mean programms.

---

### Post by howefield on 2010-02-01
Do you want to remove the application or just the package that installed it ?

---

### Post by mcduck on 2010-02-01
> **Ubunser said:**
> When I install them where does system place them? I mean programms.

contents of packages are installed all around the file system, removing anything manually is a lot of work (and will most likely just result in broken packages and non-functional package management).

If you can tell us what you are trying to accomplish I'm sure we'll be able to tell you a better way to do that.. :)

---

### Post by warfacegod on 2010-02-01
If your just looking to do a bit of sweeping up then:

```
sudo apt-get autoremove
```

---

### Post by Ubunser on 2010-02-01
I installed istanbul and foud it inoperable, so tried to uninstall it by typing "gksudo apt-get remove istanbul", but on some stage(Y/n?) the terminal freezes and the result is I close it and the program is still in menu

---

### Post by drs305 on 2010-02-01
I agree with the previous posters who recommend *not* trying to remove installed apps manually (removing the packages from /var/cache/apt/archives can be done via apt commands, one of which was already mentioned).

However, if you would just like to see where *installed* apps files are located, you can open Synaptic, highlight a package, then select Properties, Installed Files. From the command line, this command will produce slightly different results:
```
whereis <app>
```
Example: whereis gimp

---

### Post by philinux on 2010-02-01
> **Ubunser said:**
> I installed istanbul and foud it inoperable, so tried to uninstall it by typing "gksudo apt-get remove istanbul", but on some stage(Y/n?) the terminal freezes and the result is I close it and the program is still in menu

```
sudo apt-get purge instanbul
```

post back any errors. You only use gksudo to launch graphical applications.

---

### Post by warfacegod on 2010-02-01
I would second Synaptic and also recommend it for removing your istanbul app. Mark it for Complete Removal.

---

### Post by mcduck on 2010-02-01
> **Ubunser said:**
> I installed istanbul and foud it inoperable, so tried to uninstall it by typing "gksudo apt-get remove istanbul", but on some stage(Y/n?) the terminal freezes and the result is I close it and the program is still in menu

did you try running "sudo apt-get remove istanbul" again after that? If not, try that again and if it doesn't freeze then post the output here.

---

### Post by ushills on 2010-02-01
The correct way to remove and purge any configuration files is

```
sudo apt-get remove --purge *application*
```

---

### Post by t0p on 2010-02-01
> **Ubunser said:**
> I installed istanbul and foud it inoperable, so tried to uninstall it by typing "gksudo apt-get remove istanbul", but on some stage(Y/n?) the terminal freezes and the result is I close it and the program is still in menu

I don't know if this is what gave you the problem... but **apt-get** is a command-line (terminal) program, and **gksudo** is used to run graphical interface programs as root.  To remove *istanbul*, the correct command is

```
sudo apt-get remove istanbul
```Removing applications manually isn't the best way to go about it.  And the various files that make up an application are installed to a number of locations.  Take, for instance, the program *gedit*.  I can find its location with this command:

```
t0p@phobos:~$ which gedit
/usr/bin/gedit

```But that isn't the only file related to gedit, as this next command reveals:

```
t0p@phobos:~$ locate gedit
/home/t0p/.gconf/apps/gedit-2
/home/t0p/.gconf/apps/gedit-2/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences
/home/t0p/.gconf/apps/gedit-2/preferences/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences/editor
/home/t0p/.gconf/apps/gedit-2/preferences/print
/home/t0p/.gconf/apps/gedit-2/preferences/ui
/home/t0p/.gconf/apps/gedit-2/preferences/editor/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences/editor/wrap_mode
/home/t0p/.gconf/apps/gedit-2/preferences/editor/wrap_mode/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences/print/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences/print/fonts
/home/t0p/.gconf/apps/gedit-2/preferences/print/page
/home/t0p/.gconf/apps/gedit-2/preferences/print/fonts/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences/print/page/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences/ui/%gconf.xml
/home/t0p/.gconf/apps/gedit-2/preferences/ui/statusbar
/home/t0p/.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml
/home/t0p/.gconf/apps/gnome-settings/gedit
/home/t0p/.gconf/apps/gnome-settings/gedit/%gconf.xml
/home/t0p/.gnome2/accelsgedit
/home/t0p/.gnome2/gedit
/home/t0p/.gnome2/gedit-2
/home/t0p/.gnome2/gedit-metadata.xml
/home/t0p/.gnome2/gedit/gedit-page-setup
/home/t0p/.gnome2/gedit/gedit-print-settings
/home/t0p/.gnome2/gedit/sessions
/home/t0p/.gnome2/gedit/sessions/gedit-6YBsVJ
/home/t0p/.gnome2/gedit/sessions/gedit-G4MkKo
/home/t0p/.google/picasa/3.0/drive_c/windows/regedit.exe
/home/t0p/.icons/gnome-brave/16x16/apps/gedit-icon.png
/home/t0p/.icons/gnome-brave/16x16/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-brave/16x16/apps/gedit-logo.png
/home/t0p/.icons/gnome-brave/22x22/apps/gedit-icon.png
/home/t0p/.icons/gnome-brave/22x22/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-brave/22x22/apps/gedit-logo.png
/home/t0p/.icons/gnome-brave/24x24/apps/gedit-icon.png
/home/t0p/.icons/gnome-brave/24x24/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-brave/24x24/apps/gedit-logo.png
/home/t0p/.icons/gnome-brave/32x32/apps/gedit-icon.png
/home/t0p/.icons/gnome-brave/32x32/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-brave/32x32/apps/gedit-logo.png
/home/t0p/.icons/gnome-brave/scalable/apps/gedit-icon.svg
/home/t0p/.icons/gnome-brave/scalable/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-brave/scalable/apps/gedit-logo.svg
/home/t0p/.icons/gnome-wine/16x16/apps/gedit-icon.png
/home/t0p/.icons/gnome-wine/16x16/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wine/16x16/apps/gedit-logo.png
/home/t0p/.icons/gnome-wine/22x22/apps/gedit-icon.png
/home/t0p/.icons/gnome-wine/22x22/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wine/22x22/apps/gedit-logo.png
/home/t0p/.icons/gnome-wine/24x24/apps/gedit-icon.png
/home/t0p/.icons/gnome-wine/24x24/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wine/24x24/apps/gedit-logo.png
/home/t0p/.icons/gnome-wine/32x32/apps/gedit-icon.png
/home/t0p/.icons/gnome-wine/32x32/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wine/32x32/apps/gedit-logo.png
/home/t0p/.icons/gnome-wine/scalable/apps/gedit-icon.svg
/home/t0p/.icons/gnome-wine/scalable/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wine/scalable/apps/gedit-logo.svg
/home/t0p/.icons/gnome-wise/16x16/apps/gedit-icon.png
/home/t0p/.icons/gnome-wise/16x16/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wise/16x16/apps/gedit-logo.png
/home/t0p/.icons/gnome-wise/22x22/apps/gedit-icon.png
/home/t0p/.icons/gnome-wise/22x22/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wise/22x22/apps/gedit-logo.png
/home/t0p/.icons/gnome-wise/24x24/apps/gedit-icon.png
/home/t0p/.icons/gnome-wise/24x24/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wise/24x24/apps/gedit-logo.png
/home/t0p/.icons/gnome-wise/32x32/apps/gedit-icon.png
/home/t0p/.icons/gnome-wise/32x32/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wise/32x32/apps/gedit-logo.png
/home/t0p/.icons/gnome-wise/scalable/apps/gedit-icon.svg
/home/t0p/.icons/gnome-wise/scalable/apps/gedit-icon.xpm
/home/t0p/.icons/gnome-wise/scalable/apps/gedit-logo.svg
/home/t0p/.local/share/applications/gedit.desktop
/home/t0p/.ubuntu-tweak/scripts/Open with gedit
/home/t0p/.ubuntu-tweak/scripts/Open with gedit(as root)
/home/t0p/.wine/drive_c/windows/regedit.exe
/usr/bin/gedit
/usr/bin/regedit
/usr/bin/vorbistagedit
/usr/lib/gedit
/usr/lib/gedit-2
/usr/lib/gedit/gedit-2
/usr/lib/gedit/gedit-2/gedit-bugreport.sh
/usr/lib/gedit-2/plugins
/usr/lib/gedit-2/plugins/changecase.gedit-plugin
/usr/lib/gedit-2/plugins/docinfo.gedit-plugin
/usr/lib/gedit-2/plugins/externaltools
/usr/lib/gedit-2/plugins/externaltools.gedit-plugin
/usr/lib/gedit-2/plugins/filebrowser.gedit-plugin
/usr/lib/gedit-2/plugins/indent.gedit-plugin
/usr/lib/gedit-2/plugins/libchangecase.so
/usr/lib/gedit-2/plugins/libdocinfo.so
/usr/lib/gedit-2/plugins/libfilebrowser.so
/usr/lib/gedit-2/plugins/libindent.so
/usr/lib/gedit-2/plugins/libmodelines.so
/usr/lib/gedit-2/plugins/libsample.so
/usr/lib/gedit-2/plugins/libseahorse-pgp.so
/usr/lib/gedit-2/plugins/libsort.so
/usr/lib/gedit-2/plugins/libspell.so
/usr/lib/gedit-2/plugins/libtaglist.so
/usr/lib/gedit-2/plugins/libtime.so
/usr/lib/gedit-2/plugins/modelines.gedit-plugin
/usr/lib/gedit-2/plugins/pythonconsole
/usr/lib/gedit-2/plugins/pythonconsole.gedit-plugin
/usr/lib/gedit-2/plugins/sample.gedit-plugin
/usr/lib/gedit-2/plugins/seahorse-pgp.gedit-plugin
/usr/lib/gedit-2/plugins/snippets
/usr/lib/gedit-2/plugins/snippets.gedit-plugin
/usr/lib/gedit-2/plugins/sort.gedit-plugin
/usr/lib/gedit-2/plugins/spell.gedit-plugin
/usr/lib/gedit-2/plugins/taglist.gedit-plugin
/usr/lib/gedit-2/plugins/time.gedit-plugin
/usr/lib/gedit-2/plugins/externaltools/ElementTree.py
/usr/lib/gedit-2/plugins/externaltools/ElementTree.pyc
/usr/lib/gedit-2/plugins/externaltools/__init__.py
/usr/lib/gedit-2/plugins/externaltools/__init__.pyc
/usr/lib/gedit-2/plugins/externaltools/capture.py
/usr/lib/gedit-2/plugins/externaltools/capture.pyc
/usr/lib/gedit-2/plugins/externaltools/functions.py
/usr/lib/gedit-2/plugins/externaltools/functions.pyc
/usr/lib/gedit-2/plugins/externaltools/library.py
/usr/lib/gedit-2/plugins/externaltools/library.pyc
/usr/lib/gedit-2/plugins/externaltools/manager.py
/usr/lib/gedit-2/plugins/externaltools/manager.pyc
/usr/lib/gedit-2/plugins/externaltools/outputpanel.py
/usr/lib/gedit-2/plugins/externaltools/outputpanel.pyc
/usr/lib/gedit-2/plugins/externaltools/tools.glade
/usr/lib/gedit-2/plugins/pythonconsole/__init__.py
/usr/lib/gedit-2/plugins/pythonconsole/__init__.pyc
/usr/lib/gedit-2/plugins/pythonconsole/console.py
/usr/lib/gedit-2/plugins/pythonconsole/console.pyc
/usr/lib/gedit-2/plugins/snippets/Document.py
/usr/lib/gedit-2/plugins/snippets/Document.pyc
/usr/lib/gedit-2/plugins/snippets/ElementTree.py
/usr/lib/gedit-2/plugins/snippets/ElementTree.pyc
/usr/lib/gedit-2/plugins/snippets/Exporter.py
/usr/lib/gedit-2/plugins/snippets/Exporter.pyc
/usr/lib/gedit-2/plugins/snippets/Helper.py
/usr/lib/gedit-2/plugins/snippets/Helper.pyc
/usr/lib/gedit-2/plugins/snippets/Importer.py
/usr/lib/gedit-2/plugins/snippets/Importer.pyc
/usr/lib/gedit-2/plugins/snippets/Library.py
/usr/lib/gedit-2/plugins/snippets/Library.pyc
/usr/lib/gedit-2/plugins/snippets/Manager.py
/usr/lib/gedit-2/plugins/snippets/Manager.pyc
/usr/lib/gedit-2/plugins/snippets/Parser.py
/usr/lib/gedit-2/plugins/snippets/Parser.pyc
/usr/lib/gedit-2/plugins/snippets/Placeholder.py
/usr/lib/gedit-2/plugins/snippets/Placeholder.pyc
/usr/lib/gedit-2/plugins/snippets/Snippet.py
/usr/lib/gedit-2/plugins/snippets/Snippet.pyc
/usr/lib/gedit-2/plugins/snippets/SnippetComplete.py
/usr/lib/gedit-2/plugins/snippets/SnippetComplete.pyc
/usr/lib/gedit-2/plugins/snippets/SubstitutionParser.py
/usr/lib/gedit-2/plugins/snippets/SubstitutionParser.pyc
/usr/lib/gedit-2/plugins/snippets/WindowHelper.py
/usr/lib/gedit-2/plugins/snippets/WindowHelper.pyc
/usr/lib/gedit-2/plugins/snippets/__init__.py
/usr/lib/gedit-2/plugins/snippets/__init__.pyc
/usr/lib/gedit-2/plugins/snippets/snippets.glade
/usr/lib/wine/regedit.exe.so
/usr/share/gedit-2
/usr/share/app-install/desktop/gedit.desktop
/usr/share/applications/gedit.desktop
/usr/share/doc/gedit
/usr/share/doc/gedit-common
/usr/share/doc/gedit/AUTHORS
/usr/share/doc/gedit/BUGS
/usr/share/doc/gedit/NEWS.gz
/usr/share/doc/gedit/README
/usr/share/doc/gedit/changelog.Debian.gz
/usr/share/doc/gedit/copyright
/usr/share/doc/gedit-common/AUTHORS
/usr/share/doc/gedit-common/BUGS
/usr/share/doc/gedit-common/NEWS.gz
/usr/share/doc/gedit-common/README
/usr/share/doc/gedit-common/changelog.Debian.gz
/usr/share/doc/gedit-common/copyright
/usr/share/gconf/schemas/gedit-file-browser.schemas
/usr/share/gconf/schemas/gedit.schemas
/usr/share/gconf/schemas/seahorse-gedit.schemas
/usr/share/gedit-2/glade
/usr/share/gedit-2/icons
/usr/share/gedit-2/logo
/usr/share/gedit-2/plugins
/usr/share/gedit-2/taglist
/usr/share/gedit-2/ui
/usr/share/gedit-2/glade/docinfo.glade2
/usr/share/gedit-2/glade/gedit-encodings-dialog.glade
/usr/share/gedit-2/glade/gedit-open-location-dialog.glade
/usr/share/gedit-2/glade/gedit-preferences-dialog.glade
/usr/share/gedit-2/glade/gedit-print-preferences.glade
/usr/share/gedit-2/glade/gedit-search-dialog.glade
/usr/share/gedit-2/glade/languages-dialog.glade2
/usr/share/gedit-2/glade/sort.glade2
/usr/share/gedit-2/glade/spell-checker.glade2
/usr/share/gedit-2/glade/time.glade2
/usr/share/gedit-2/icons/gedit-plugin.png
/usr/share/gedit-2/logo/gedit-logo.png
/usr/share/gedit-2/plugins/filebrowser
/usr/share/gedit-2/plugins/snippets
/usr/share/gedit-2/plugins/tools
/usr/share/gedit-2/plugins/filebrowser/gedit-file-browser-widget-ui.xml
/usr/share/gedit-2/plugins/snippets/c++.xml
/usr/share/gedit-2/plugins/snippets/c.xml
/usr/share/gedit-2/plugins/snippets/css.xml
/usr/share/gedit-2/plugins/snippets/docbook.xml
/usr/share/gedit-2/plugins/snippets/global.xml
/usr/share/gedit-2/plugins/snippets/haskell.xml
/usr/share/gedit-2/plugins/snippets/html.xml
/usr/share/gedit-2/plugins/snippets/idl.xml
/usr/share/gedit-2/plugins/snippets/java.xml
/usr/share/gedit-2/plugins/snippets/javascript.xml
/usr/share/gedit-2/plugins/snippets/lang
/usr/share/gedit-2/plugins/snippets/latex.xml
/usr/share/gedit-2/plugins/snippets/perl.xml
/usr/share/gedit-2/plugins/snippets/php.xml
/usr/share/gedit-2/plugins/snippets/python.xml
/usr/share/gedit-2/plugins/snippets/ruby.xml
/usr/share/gedit-2/plugins/snippets/sh.xml
/usr/share/gedit-2/plugins/snippets/snippets.xml
/usr/share/gedit-2/plugins/snippets/tcl.xml
/usr/share/gedit-2/plugins/snippets/xml.xml
/usr/share/gedit-2/plugins/snippets/lang/snippets.lang
/usr/share/gedit-2/plugins/tools/build
/usr/share/gedit-2/plugins/tools/open-terminal-here
/usr/share/gedit-2/plugins/tools/remove-trailing-spaces
/usr/share/gedit-2/plugins/tools/run-command
/usr/share/gedit-2/taglist/HTML.tags.gz
/usr/share/gedit-2/taglist/Latex.tags.gz
/usr/share/gedit-2/taglist/XSLT.tags.gz
/usr/share/gedit-2/taglist/XUL.tags.gz
/usr/share/gedit-2/ui/gedit-ui.xml
/usr/share/gnome/help/gedit
/usr/share/gnome/help/gedit/C
/usr/share/gnome/help/gedit/bg
/usr/share/gnome/help/gedit/de
/usr/share/gnome/help/gedit/es
/usr/share/gnome/help/gedit/eu
/usr/share/gnome/help/gedit/fr
/usr/share/gnome/help/gedit/hu
/usr/share/gnome/help/gedit/it
/usr/share/gnome/help/gedit/ja
/usr/share/gnome/help/gedit/ko
/usr/share/gnome/help/gedit/oc
/usr/share/gnome/help/gedit/pt_BR
/usr/share/gnome/help/gedit/ro
/usr/share/gnome/help/gedit/ru
/usr/share/gnome/help/gedit/sv
/usr/share/gnome/help/gedit/uk
/usr/share/gnome/help/gedit/zh_CN
/usr/share/gnome/help/gedit/zh_HK
/usr/share/gnome/help/gedit/zh_TW
/usr/share/gnome/help/gedit/C/figures
/usr/share/gnome/help/gedit/C/gedit.xml
/usr/share/gnome/help/gedit/C/legal.xml
/usr/share/gnome/help/gedit/C/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/C/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/C/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/C/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/C/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/C/figures/gedit_window.png
/usr/share/gnome/help/gedit/bg/figures
/usr/share/gnome/help/gedit/bg/gedit.xml
/usr/share/gnome/help/gedit/bg/legal.xml
/usr/share/gnome/help/gedit/bg/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/bg/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/bg/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/bg/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/bg/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/bg/figures/gedit_window.png
/usr/share/gnome/help/gedit/de/figures
/usr/share/gnome/help/gedit/de/gedit.xml
/usr/share/gnome/help/gedit/de/legal.xml
/usr/share/gnome/help/gedit/de/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/de/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/de/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/de/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/de/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/de/figures/gedit_window.png
/usr/share/gnome/help/gedit/es/figures
/usr/share/gnome/help/gedit/es/gedit.xml
/usr/share/gnome/help/gedit/es/legal.xml
/usr/share/gnome/help/gedit/es/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/es/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/es/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/es/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/es/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/es/figures/gedit_window.png
/usr/share/gnome/help/gedit/eu/figures
/usr/share/gnome/help/gedit/eu/gedit.xml
/usr/share/gnome/help/gedit/eu/legal.xml
/usr/share/gnome/help/gedit/eu/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/eu/figures/gedit_window.png
/usr/share/gnome/help/gedit/fr/figures
/usr/share/gnome/help/gedit/fr/gedit.xml
/usr/share/gnome/help/gedit/fr/legal.xml
/usr/share/gnome/help/gedit/fr/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/fr/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/fr/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/fr/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/fr/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/fr/figures/gedit_window.png
/usr/share/gnome/help/gedit/hu/figures
/usr/share/gnome/help/gedit/hu/gedit.xml
/usr/share/gnome/help/gedit/hu/legal.xml
/usr/share/gnome/help/gedit/hu/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/hu/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/hu/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/hu/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/hu/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/hu/figures/gedit_window.png
/usr/share/gnome/help/gedit/it/figures
/usr/share/gnome/help/gedit/it/gedit.xml
/usr/share/gnome/help/gedit/it/legal.xml
/usr/share/gnome/help/gedit/it/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/it/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/it/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/it/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/it/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/it/figures/gedit_window.png
/usr/share/gnome/help/gedit/ja/figures
/usr/share/gnome/help/gedit/ja/gedit.xml
/usr/share/gnome/help/gedit/ja/legal.xml
/usr/share/gnome/help/gedit/ja/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/ja/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/ja/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/ja/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/ja/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/ja/figures/gedit_window.png
/usr/share/gnome/help/gedit/ko/figures
/usr/share/gnome/help/gedit/ko/gedit.xml
/usr/share/gnome/help/gedit/ko/legal.xml
/usr/share/gnome/help/gedit/ko/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/ko/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/ko/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/ko/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/ko/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/ko/figures/gedit_window.png
/usr/share/gnome/help/gedit/oc/figures
/usr/share/gnome/help/gedit/oc/gedit.xml
/usr/share/gnome/help/gedit/oc/legal.xml
/usr/share/gnome/help/gedit/oc/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/oc/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/oc/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/oc/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/oc/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/oc/figures/gedit_window.png
/usr/share/gnome/help/gedit/pt_BR/figures
/usr/share/gnome/help/gedit/pt_BR/gedit.xml
/usr/share/gnome/help/gedit/pt_BR/legal.xml
/usr/share/gnome/help/gedit/pt_BR/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/pt_BR/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/pt_BR/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/pt_BR/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/pt_BR/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/pt_BR/figures/gedit_window.png
/usr/share/gnome/help/gedit/ro/figures
/usr/share/gnome/help/gedit/ro/gedit.xml
/usr/share/gnome/help/gedit/ro/legal.xml
/usr/share/gnome/help/gedit/ro/figures/gedit_window.png
/usr/share/gnome/help/gedit/ru/figures
/usr/share/gnome/help/gedit/ru/gedit.xml
/usr/share/gnome/help/gedit/ru/legal.xml
/usr/share/gnome/help/gedit/ru/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/ru/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/ru/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/ru/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/ru/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/ru/figures/gedit_window.png
/usr/share/gnome/help/gedit/sv/figures
/usr/share/gnome/help/gedit/sv/gedit.xml
/usr/share/gnome/help/gedit/sv/legal.xml
/usr/share/gnome/help/gedit/sv/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/sv/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/sv/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/sv/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/sv/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/sv/figures/gedit_window.png
/usr/share/gnome/help/gedit/uk/figures
/usr/share/gnome/help/gedit/uk/gedit.xml
/usr/share/gnome/help/gedit/uk/legal.xml
/usr/share/gnome/help/gedit/uk/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/uk/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/uk/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/uk/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/uk/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/uk/figures/gedit_window.png
/usr/share/gnome/help/gedit/zh_CN/figures
/usr/share/gnome/help/gedit/zh_CN/gedit.xml
/usr/share/gnome/help/gedit/zh_CN/legal.xml
/usr/share/gnome/help/gedit/zh_CN/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/zh_CN/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/zh_CN/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/zh_CN/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/zh_CN/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/zh_CN/figures/gedit_window.png
/usr/share/gnome/help/gedit/zh_HK/figures
/usr/share/gnome/help/gedit/zh_HK/gedit.xml
/usr/share/gnome/help/gedit/zh_HK/legal.xml
/usr/share/gnome/help/gedit/zh_HK/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/zh_HK/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/zh_HK/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/zh_HK/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/zh_HK/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/zh_HK/figures/gedit_window.png
/usr/share/gnome/help/gedit/zh_TW/figures
/usr/share/gnome/help/gedit/zh_TW/gedit.xml
/usr/share/gnome/help/gedit/zh_TW/legal.xml
/usr/share/gnome/help/gedit/zh_TW/figures/gedit_format_bold.png
/usr/share/gnome/help/gedit/zh_TW/figures/gedit_format_italic.png
/usr/share/gnome/help/gedit/zh_TW/figures/gedit_format_strikethrough.png
/usr/share/gnome/help/gedit/zh_TW/figures/gedit_format_underline.png
/usr/share/gnome/help/gedit/zh_TW/figures/gedit_recent_files_menu_icon.png
/usr/share/gnome/help/gedit/zh_TW/figures/gedit_window.png
/usr/share/gnome/help/user-guide/C/figures/gedit_window.png
/usr/share/gnome/help/user-guide/ar/figures/gedit_window.png
/usr/share/gnome/help/user-guide/bg/figures/gedit_window.png
/usr/share/gnome/help/user-guide/de/figures/gedit_window.png
/usr/share/gnome/help/user-guide/el/figures/gedit_window.png
/usr/share/gnome/help/user-guide/es/figures/gedit_window.png
/usr/share/gnome/help/user-guide/fi/figures/gedit_window.png
/usr/share/gnome/help/user-guide/fr/figures/gedit_window.png
/usr/share/gnome/help/user-guide/hu/figures/gedit_window.png
/usr/share/gnome/help/user-guide/it/figures/gedit_window.png
/usr/share/gnome/help/user-guide/ko/figures/gedit_window.png
/usr/share/gnome/help/user-guide/oc/figures/gedit_window.png
/usr/share/gnome/help/user-guide/pa/figures/gedit_window.png
/usr/share/gnome/help/user-guide/pt/figures/gedit_window.png
/usr/share/gnome/help/user-guide/pt_BR/figures/gedit_window.png
/usr/share/gnome/help/user-guide/ru/figures/gedit_window.png
/usr/share/gnome/help/user-guide/sv/figures/gedit_window.png
/usr/share/gnome/help/user-guide/zh_CN/figures/gedit_window.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/gedit-icon.png
/usr/share/icons/crystalsvg/16x16/apps/dlgedit.png
/usr/share/icons/crystalsvg/32x32/apps/dlgedit.png
/usr/share/icons/mono/scalable/apps/dlgedit.svgz
/usr/share/lintian/overrides/gedit
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gedit.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gedit.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gedit.mo
/usr/share/man/man1/gedit.1.gz
/usr/share/man/man1/vorbistagedit.1.gz
/usr/share/menu/gedit
/usr/share/omf/gedit
/usr/share/omf/gedit/gedit-C.omf
/usr/share/omf/gedit/gedit-bg.omf
/usr/share/omf/gedit/gedit-de.omf
/usr/share/omf/gedit/gedit-es.omf
/usr/share/omf/gedit/gedit-eu.omf
/usr/share/omf/gedit/gedit-fr.omf
/usr/share/omf/gedit/gedit-hu.omf
/usr/share/omf/gedit/gedit-it.omf
/usr/share/omf/gedit/gedit-ja.omf
/usr/share/omf/gedit/gedit-ko.omf
/usr/share/omf/gedit/gedit-oc.omf
/usr/share/omf/gedit/gedit-pt_BR.omf
/usr/share/omf/gedit/gedit-ro.omf
/usr/share/omf/gedit/gedit-ru.omf
/usr/share/omf/gedit/gedit-sv.omf
/usr/share/omf/gedit/gedit-uk.omf
/usr/share/omf/gedit/gedit-zh_CN.omf
/usr/share/omf/gedit/gedit-zh_HK.omf
/usr/share/omf/gedit/gedit-zh_TW.omf
/usr/share/pixmaps/gedit-icon.xpm
/usr/share/python-support/gedit.dirs
/usr/share/python-support/gnome-orca/orca/scripts/gedit.py
/usr/share/ubuntu-tweak/data/scripts/Open with gedit
/usr/share/ubuntu-tweak/data/scripts/Open with gedit(as root)
/var/lib/dpkg/info/gedit-common.list
/var/lib/dpkg/info/gedit-common.md5sums
/var/lib/dpkg/info/gedit-common.postinst
/var/lib/dpkg/info/gedit-common.postrm
/var/lib/dpkg/info/gedit.list
/var/lib/dpkg/info/gedit.md5sums
/var/lib/dpkg/info/gedit.postinst
/var/lib/dpkg/info/gedit.postrm
/var/lib/dpkg/info/gedit.prerm
/var/lib/python-support/python2.5/orca/scripts/gedit.py
/var/lib/python-support/python2.5/orca/scripts/gedit.pyc

```Now, I suppose I *could* sit here and manually delete each file in turn.  But that wouldn't be such a good idea.  For instance, if you remove a program by using *apt-get*, the system's database of installed packages is updated to reflect the fact thatthe program has gone.  If you delete it all manually, the apt database is not updated.

---

### Post by Ubunser on 2010-02-01
> **mcduck said:**
> did you try running "sudo apt-get remove istanbul" again after that? If not, try that again and if it doesn't freeze then post the output here.

I used that and it's gone, thanks. I thought I could use gksudo, thanks for help.

---

### Post by Ubunser on 2010-02-01
Thanks, t0p now I got it. I saw that list in synaptic, it is huge

---

