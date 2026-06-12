---
title: "tar.gz woes (again) - installing cb2bib"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by loobyloo on 2009-01-22
Hi

I'm having some problems installing cb2bib.  It's something which I'm hoping will help get a bibliography I've done into Zotero without having to manually type in over 100 references.

I downloaded the tar.gz to the desktop then extracted the files to /home/cliff/.c2bib

Following the instructions on [http://www.molspaces.com/d_cb2bib-installation.php](http://www.molspaces.com/d_cb2bib-installation.php)
I can't unpack the file by using tar -xzvf cb2bib-1.1.0.tar.gz

When I do I get 

cliff@cliff-laptop:~$ tar -xzvf cb2bib-1.1.0.tar.gz
tar: cb2bib-1.1.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
cliff@cliff-laptop:~$ 

Probably something straighforward but if anyone cuold point out where I'm going wrong I'd be most grateful.

---

### Post by Titan8990 on 2009-01-22
Looks like the filename is wrong. You should use tab to autocomplete names such as that one.

Lets see a ls -al of that directory.

---

### Post by loobyloo on 2009-01-22
Er....ls-al ?

You mean:
drwxr-xr-x  3 cliff cliff   4096 2009-01-22 11:42 .c2bib

---

### Post by taurus on 2009-01-22
How about

```
cd .c2bib
ls -la
```

---

### Post by perlluver on 2009-01-22
> **loobyloo said:**
> Hi

I'm having some problems installing cb2bib.  It's something which I'm hoping will help get a bibliography I've done into Zotero without having to manually type in over 100 references.

I downloaded the tar.gz to the desktop then extracted the files to /home/cliff/.c2bib

Following the instructions on [http://www.molspaces.com/d_cb2bib-installation.php](http://www.molspaces.com/d_cb2bib-installation.php)
I can't unpack the file by using tar -xzvf cb2bib-1.1.0.tar.gz

When I do I get 

cliff@cliff-laptop:~$ tar -xzvf cb2bib-1.1.0.tar.gz
tar: cb2bib-1.1.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
cliff@cliff-laptop:~$ 

Probably something straighforward but if anyone cuold point out where I'm going wrong I'd be most grateful.

It appears you are in the wrong directory when you tried to Un-Tar.  ```
cd /home/cliff/.c2bib
``` then try to untar it.

---

### Post by loobyloo on 2009-01-22
> **perlluver said:**
> It appears you are in the wrong directory when you tried to Un-Tar.  ```
cd /home/cliff/.c2bib
``` then try to untar it.

That gives me

cliff@cliff-laptop:~$ cd /home/cliff/.c2bib
cliff@cliff-laptop:~/.c2bib$ tar -xzvf cb2bib-1.1.0.tar.gz
tar: cb2bib-1.1.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by loobyloo on 2009-01-22
> **taurus said:**
> How about

```
cd .c2bib
ls -la
```

That gives

cliff@cliff-laptop:~$ cd .c2bib
cliff@cliff-laptop:~/.c2bib$ ls -la
total 12
drwxr-xr-x  3 cliff cliff 4096 2009-01-22 11:42 .
drwxr-xr-x 79 cliff cliff 4096 2009-01-22 15:03 ..
drwxr-xr-x  6 cliff cliff 4096 2009-01-22 11:43 cb2bib-1.1.0
cliff@cliff-laptop:~/.c2bib$

---

### Post by Titan8990 on 2009-01-22
You don't have the tar.gz but appears you have the already unarchived directory....

---

### Post by taurus on 2009-01-22
Now

```
cd cb2bib-1.1.0
ls -la
```

---

### Post by loobyloo on 2009-01-22
> **taurus said:**
> Now

```
cd cb2bib-1.1.0
ls -la
```

That gives

cliff@cliff-laptop:~$ cd cb2bib-1.1.0
bash: cd: cb2bib-1.1.0: No such file or directory
cliff@cliff-laptop:~$ ls -la

---

### Post by DFord425 on 2009-01-22
> **loobyloo said:**
> That gives

cliff@cliff-laptop:~$ cd cb2bib-1.1.0
bash: cd: cb2bib-1.1.0: No such file or directory
cliff@cliff-laptop:~$ ls -la

run the cd cb2bib-1.1.0 from this directory: cliff@cliff-laptop:~/.c2bib$

---

### Post by loobyloo on 2009-01-22
Thanks everyone - I will do, in about 1.5 hours - got a seminar now.

---

### Post by loobyloo on 2009-01-22
I'm very grateful for your painstaking help and the way you responded, but I can't be bothered with it all any more.  I'm going to type the references manually into Zotero.

This disjunction between the willingness of others to help and the hours of frustration that moderately IT-literate people like myself have in trying to do something that would be simple in Windows illustrates the reasons why people don't bother with Linux.

---

### Post by handydan918 on 2009-01-22
I would be surprised if you couldn't find this package as a .deb.
Even if you can't, I bet you could find someone to package it for you.

---

### Post by darksideforge on 2009-01-22
> **loobyloo said:**
> I'm very grateful for your painstaking help and the way you responded, but I can't be bothered with it all any more.  I'm going to type the references manually into Zotero.

This disjunction between the willingness of others to help and the hours of frustration that moderately IT-literate people like myself have in trying to do something that would be simple in Windows illustrates the reasons why people don't bother with Linux.


Cliff,
I was loving your thread right up until this point. I just wonder how many Euro's you'd be spending for that Micro$h*t program that would compile that database for you...any idea? Even as sorry as our US $ is these days, I'd bet you'd be paying a pretty penny for it, and that's IF you could even find one. The last time I checked, a full-blown Windows Vista Premium Install (which would give you the authoring rights for the M$Access program you'd have to create) would cost you about $300US...and that's still a nice chunk of change in EU isn't it?

I feel your pain...I've been trying to install tar balls (.tar) files that I downloaded 2 months ago and STILL can't get it right on my Toshiba Laptop....BUT!!!! at least I'm learning while I'm at it...and loving the learning. As you're in a seminar today/tonight, I can only imagine that you enjoy learning as well.  Isn't the end-result worth it? It is for me.

Good Luck.

---

### Post by loobyloo on 2009-01-23
Yes, I know, you're totally right...but you know that point at which the frustration at one's lack of knowledge and ability becomes impossible to suppress - well I hit it! :)  

I'll have another go at it in a week or two and try to keep calmer.

---

### Post by mali2297 on 2009-01-23
The program depends on Qt4, so I think that you need to install the package libqt4-dev first. From the terminal, run
```

sudo apt-get install libqt4-dev

```
or use the package manager Synaptic.

Then fetch the tarball directly with
```

wget http://www.molspaces.com/dl/progs/cb2bib-1.1.0.tar.gz

```
Extract..
```

tar xvf cb2bib-1.1.0.tar.gz

```
Go to the source directory..
```

cd cb2bib-1.1.0/

```
Configure..
```

./configure --prefix /usr/local

```
If there are no errors, continue with building the program..
```

make

```
Last, install it..
```

sudo make install

```

---

### Post by loobyloo on 2009-01-23
Thanks Martin... The lib thing is already installed, but I can only get as far as...

cliff@cliff-laptop:~$ wget [http://www.molspaces.com/dl/progs/cb2bib-1.1.0.tar.gz--2009-01-23](http://www.molspaces.com/dl/progs/cb2bib-1.1.0.tar.gz--2009-01-23) 12:10:13--  [http://www.molspaces.com/dl/progs/cb2bib-1.1.0.tar.gz](http://www.molspaces.com/dl/progs/cb2bib-1.1.0.tar.gz)
Resolving [www.molspaces.com](www.molspaces.com)... 74.54.25.194
Connecting to [www.molspaces.com|74.54.25.194|:80](www.molspaces.com|74.54.25.194|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 463665 (453K) [application/x-gzip]
Saving to: `cb2bib-1.1.0.tar.gz'

100%[======================================>] 463,665      291K/s   in 1.6s    

2009-01-23 12:10:15 (291 KB/s) - `cb2bib-1.1.0.tar.gz' saved [463665/463665]

cliff@cliff-laptop:~$ cd cb2bib-1.1.0
bash: cd: cb2bib-1.1.0: No such file or directory

---

### Post by loobyloo on 2009-01-23
Oops!  Missing out a stage.

OK, again...

cliff@cliff-laptop:~$ tar xvf cb2bib-1.1.0.tar.gz
cb2bib-1.1.0/
cb2bib-1.1.0/cb2bib.rc
cb2bib-1.1.0/LICENSE
cb2bib-1.1.0/src/
cb2bib-1.1.0/src/c2bSearchInFilesPattern.ui
cb2bib-1.1.0/src/c2bExport.cpp
cb2bib-1.1.0/src/c2bBibSearcherCache.cpp
cb2bib-1.1.0/src/c2bComboBox.h
cb2bib-1.1.0/src/c2bColors.h
cb2bib-1.1.0/src/cb2bib.qrc
cb2bib-1.1.0/src/c2bEditor.ui
cb2bib-1.1.0/src/c2bConfigure.h
cb2bib-1.1.0/src/c2bBibSearcher.h
cb2bib-1.1.0/src/c2bConfigureFR.cpp
cb2bib-1.1.0/src/c2bCiteIDLineEdit.h
cb2bib-1.1.0/src/c2bMetaPreparser.h
cb2bib-1.1.0/src/c2bClipboard.h
cb2bib-1.1.0/src/icons/
cb2bib-1.1.0/src/icons/application-x-pdf.png
cb2bib-1.1.0/src/icons/annote.png
cb2bib-1.1.0/src/icons/exit.png
cb2bib-1.1.0/src/icons/select.png
cb2bib-1.1.0/src/icons/application-x-executable.png
cb2bib-1.1.0/src/icons/cb2bib.ico
cb2bib-1.1.0/src/icons/clear_left.png
cb2bib-1.1.0/src/icons/viewZoomOut.png
cb2bib-1.1.0/src/icons/configure_fonts.png
cb2bib-1.1.0/src/icons/cb2bib.icns
cb2bib-1.1.0/src/icons/connect_established.png
cb2bib-1.1.0/src/icons/viewbib.png
cb2bib-1.1.0/src/icons/cb2bib.png
cb2bib-1.1.0/src/icons/viewForward.png
cb2bib-1.1.0/src/icons/application-x-txt.png
cb2bib-1.1.0/src/icons/filesave.png
cb2bib-1.1.0/src/icons/edit.png
cb2bib-1.1.0/src/icons/viewcb.png
cb2bib-1.1.0/src/icons/configure_files.png
cb2bib-1.1.0/src/icons/configure_network.png
cb2bib-1.1.0/src/icons/viewReload.png
cb2bib-1.1.0/src/icons/configure_documents.png
cb2bib-1.1.0/src/icons/configure_clipboard.png
cb2bib-1.1.0/src/icons/package_network.png
cb2bib-1.1.0/src/icons/add.png
cb2bib-1.1.0/src/icons/fileopen.png
cb2bib-1.1.0/src/icons/help_22.png
cb2bib-1.1.0/src/icons/configure.png
cb2bib-1.1.0/src/icons/configure_bibtex.png
cb2bib-1.1.0/src/icons/filesaveas.png
cb2bib-1.1.0/src/icons/viewZoomIn.png
cb2bib-1.1.0/src/icons/application-x-none.png
cb2bib-1.1.0/src/icons/edit16.png
cb2bib-1.1.0/src/icons/mimeFolder.png
cb2bib-1.1.0/src/icons/viewBackward.png
cb2bib-1.1.0/src/icons/fileclose_22.png
cb2bib-1.1.0/src/icons/filter.png
cb2bib-1.1.0/src/icons/connect_no.png
cb2bib-1.1.0/src/icons/tex.png
cb2bib-1.1.0/src/icons/back_cb2bib_32.png
cb2bib-1.1.0/src/icons/viewHome.png
cb2bib-1.1.0/src/icons/application-x-html.png
cb2bib-1.1.0/src/icons/configure_utilities.png
cb2bib-1.1.0/src/icons/pdf.png
cb2bib-1.1.0/src/icons/exec_22.png
cb2bib-1.1.0/src/icons/application-x-tex.png
cb2bib-1.1.0/src/c2bConsole.cpp
cb2bib-1.1.0/src/c2bNetworkQuery.cpp
cb2bib-1.1.0/src/c2bRLWebSearchSettings.ui
cb2bib-1.1.0/src/c2bNetworkQuery.h
cb2bib-1.1.0/src/c2bAnnote.h
cb2bib-1.1.0/src/c2bPostprocess.cpp
cb2bib-1.1.0/src/cb2Bib.cpp
cb2bib-1.1.0/src/c2bSearchInFiles.cpp
cb2bib-1.1.0/src/c2bNetwork.cpp
cb2bib-1.1.0/src/c2bBibHighlighter.cpp
cb2bib-1.1.0/src/c2b/
cb2bib-1.1.0/src/c2b/approximatePattern.h
cb2bib-1.1.0/src/c2b/authorString.h
cb2bib-1.1.0/src/c2b/journalDB.h
cb2bib-1.1.0/src/c2b/compositePattern.h
cb2bib-1.1.0/src/c2b/compositePattern.cpp
cb2bib-1.1.0/src/c2b/texParser.h
cb2bib-1.1.0/src/c2b/cb2bib_utilities.h
cb2bib-1.1.0/src/c2b/settings.h
cb2bib-1.1.0/src/c2b/citeIDMaker.cpp
cb2bib-1.1.0/src/c2b/bibParser.h
cb2bib-1.1.0/src/c2b/wordPattern.cpp
cb2bib-1.1.0/src/c2b/coreBibParser.h
cb2bib-1.1.0/src/c2b/settings.cpp
cb2bib-1.1.0/src/c2b/bibPreparser.cpp
cb2bib-1.1.0/src/c2b/approximatePattern.cpp
cb2bib-1.1.0/src/c2b/bibParser.cpp
cb2bib-1.1.0/src/c2b/coreBibParser.cpp
cb2bib-1.1.0/src/c2b/authorString.cpp
cb2bib-1.1.0/src/c2b/bibReference.h
cb2bib-1.1.0/src/c2b/txt/
cb2bib-1.1.0/src/c2b/txt/suffixes.txt
cb2bib-1.1.0/src/c2b/txt/prefixes.txt
cb2bib-1.1.0/src/c2b/bibPreparser.h
cb2bib-1.1.0/src/c2b/c2blib.pro
cb2bib-1.1.0/src/c2b/preprocess.cpp
cb2bib-1.1.0/src/c2b/heuristicBibParser.cpp
cb2bib-1.1.0/src/c2b/wordPattern.h
cb2bib-1.1.0/src/c2b/cb2bib_utilities.cpp
cb2bib-1.1.0/src/c2b/citeIDMaker.h
cb2bib-1.1.0/src/c2b/preprocess.h
cb2bib-1.1.0/src/c2b/c2blib.qrc
cb2bib-1.1.0/src/c2b/heuristicBibParser.h
cb2bib-1.1.0/src/c2b/texToHtml.cpp
cb2bib-1.1.0/src/c2b/texToHtml.h
cb2bib-1.1.0/src/c2b/cb2bib_parameters.h
cb2bib-1.1.0/src/c2b/htm/
cb2bib-1.1.0/src/c2b/htm/tex2html_index.html
cb2bib-1.1.0/src/c2b/htm/tex2html_jsmath_head.html
cb2bib-1.1.0/src/c2b/htm/reference_list.html
cb2bib-1.1.0/src/c2b/htm/tex2html.css
cb2bib-1.1.0/src/c2b/htm/reference_item.html
cb2bib-1.1.0/src/c2b/htm/tex2html.html
cb2bib-1.1.0/src/c2b/journalDB.cpp
cb2bib-1.1.0/src/c2b/texParser.cpp
cb2bib-1.1.0/src/c2b/monthDB.cpp
cb2bib-1.1.0/src/c2b/monthDB.h
cb2bib-1.1.0/src/c2bExportDialog.ui
cb2bib-1.1.0/src/c2bTextEdit.cpp
cb2bib-1.1.0/src/c2bSearchInFilesPatternEdit.ui
cb2bib-1.1.0/src/c2bPdfImport.ui
cb2bib-1.1.0/src/c2bSearchInFiles.h
cb2bib-1.1.0/src/c2bColors.cpp
cb2bib-1.1.0/src/c2bBibHighlighter.h
cb2bib-1.1.0/src/c2bClipboard.cpp
cb2bib-1.1.0/src/c2bPdfImport.h
cb2bib-1.1.0/src/c2bTextBrowser.cpp
cb2bib-1.1.0/src/c2bUtils.h
cb2bib-1.1.0/src/c2bSearchInFilesPattern.h
cb2bib-1.1.0/src/findDialog.ui
cb2bib-1.1.0/src/c2bRLWebSearchSettings.cpp
cb2bib-1.1.0/src/c2bEditor.h
cb2bib-1.1.0/src/c2bHighlighter.cpp
cb2bib-1.1.0/src/c2bSettings.cpp
cb2bib-1.1.0/src/c2bExport.h
cb2bib-1.1.0/src/c2bPostprocess.h
cb2bib-1.1.0/src/src.pro
cb2bib-1.1.0/src/c2bFileDialog.h
cb2bib-1.1.0/src/clipboardPoll.cpp
cb2bib-1.1.0/src/c2bReferenceList.ui
cb2bib-1.1.0/src/c2bNetwork.h
cb2bib-1.1.0/src/c2bSettings.h
cb2bib-1.1.0/src/c2bExportDialog.h
cb2bib-1.1.0/src/c2bEditor.cpp
cb2bib-1.1.0/src/c2bLineEdit.h
cb2bib-1.1.0/src/c2bConfigureFR.h
cb2bib-1.1.0/src/findDialog.h
cb2bib-1.1.0/src/c2bBibParser.h
cb2bib-1.1.0/src/c2bReferenceList.cpp
cb2bib-1.1.0/src/c2bPdfImport.cpp
cb2bib-1.1.0/src/c2bLogWidget.ui
cb2bib-1.1.0/src/c2bSearchInFiles.ui
cb2bib-1.1.0/src/c2bBibPreparserLog.h
cb2bib-1.1.0/src/cb2Bib.ui
cb2bib-1.1.0/src/c2bMetaPreparser.cpp
cb2bib-1.1.0/src/c2bWebBrowser.cpp
cb2bib-1.1.0/src/c2bConfigureFR.ui
cb2bib-1.1.0/src/c2bBibSearcherCache.h
cb2bib-1.1.0/src/c2bFileDialog.cpp
cb2bib-1.1.0/src/c2bSearchInFilesPattern.cpp
cb2bib-1.1.0/src/c2bClipEdit.cpp
cb2bib-1.1.0/src/bookmarkPlugin.h
cb2bib-1.1.0/src/c2bClipEdit.h
cb2bib-1.1.0/src/c2bConfigure.cpp
cb2bib-1.1.0/src/c2bSearchPattern.h
cb2bib-1.1.0/src/c2bNetworkQueryInfo.cpp
cb2bib-1.1.0/src/c2bLineEdit.cpp
cb2bib-1.1.0/src/c2bComboBox.cpp
cb2bib-1.1.0/src/cb2Bib.h
cb2bib-1.1.0/src/c2bUpdateMetadata.cpp
cb2bib-1.1.0/src/findDialog.cpp
cb2bib-1.1.0/src/clipboardPoll.h
cb2bib-1.1.0/src/c2bREHighlighter.h
cb2bib-1.1.0/src/c2bUtils.cpp
cb2bib-1.1.0/src/c2bReferenceList.h
cb2bib-1.1.0/src/c2bSearchPattern.cpp
cb2bib-1.1.0/src/c2bNetworkQueryInfo.h
cb2bib-1.1.0/src/c2bHighlighter.h
cb2bib-1.1.0/src/c2bWebBrowser.h
cb2bib-1.1.0/src/c2bTextBrowser.h
cb2bib-1.1.0/src/c2b.h
cb2bib-1.1.0/src/c2bConfigure.ui
cb2bib-1.1.0/src/c2b.cpp
cb2bib-1.1.0/src/c2bSaveRegExp.h
cb2bib-1.1.0/src/c2bCiteIDLineEdit.cpp
cb2bib-1.1.0/src/c2bBibParser.cpp
cb2bib-1.1.0/src/c2bConsole.h
cb2bib-1.1.0/src/c2bSaveRegExp.ui
cb2bib-1.1.0/src/main.cpp
cb2bib-1.1.0/src/c2bREHighlighter.cpp
cb2bib-1.1.0/src/xml/
cb2bib-1.1.0/src/xml/cb2bib.xmp
cb2bib-1.1.0/src/xml/ExifTool_config
cb2bib-1.1.0/src/c2bUpdateMetadata.h
cb2bib-1.1.0/src/c2bExportDialog.cpp
cb2bib-1.1.0/src/c2bTextEdit.h
cb2bib-1.1.0/src/c2bRLWebSearchSettings.h
cb2bib-1.1.0/src/c2bBibPreparserLog.cpp
cb2bib-1.1.0/src/bookmarkPlugin.cpp
cb2bib-1.1.0/src/c2bBibSearcher.cpp
cb2bib-1.1.0/src/c2bAnnote.cpp
cb2bib-1.1.0/src/htm/
cb2bib-1.1.0/src/htm/references.css
cb2bib-1.1.0/src/htm/references.html
cb2bib-1.1.0/src/htm/bib_item.html
cb2bib-1.1.0/src/c2bSaveRegExp.cpp
cb2bib-1.1.0/dl_cb2bib.desktop
cb2bib-1.1.0/AUTHORS
cb2bib-1.1.0/COPYRIGHT
cb2bib-1.1.0/c2btools/
cb2bib-1.1.0/c2btools/dl_cb2bib
cb2bib-1.1.0/c2btools/bib2pdf
cb2bib-1.1.0/c2btools/isi2bib
cb2bib-1.1.0/c2btools/ris2bib
cb2bib-1.1.0/testPDFImport/
cb2bib-1.1.0/testPDFImport/nomeaning4.pdf
cb2bib-1.1.0/testPDFImport/metadata_bibtex.pdf
cb2bib-1.1.0/testPDFImport/nomeaning1.pdf
cb2bib-1.1.0/testPDFImport/nomeaning2.pdf
cb2bib-1.1.0/testPDFImport/nomeaning3.pdf
cb2bib-1.1.0/configure
cb2bib-1.1.0/data/
cb2bib-1.1.0/data/regexps.txt
cb2bib-1.1.0/data/tex2html.css
cb2bib-1.1.0/data/references.css
cb2bib-1.1.0/data/netqinf.txt
cb2bib-1.1.0/data/abbreviations.txt
cb2bib-1.1.0/data/contributed_re.txt
cb2bib-1.1.0/cb2bib.pro
cb2bib-1.1.0/cb2bib.desktop
cliff@cliff-laptop:~$ cd cb2bib-1.1.0/
cliff@cliff-laptop:~/cb2bib-1.1.0$ ./configure --prefix/usr/local

Configuration script for cb2Bib (Unix/Linux/MacOSX)

--prefix/usr/local: unknown argument
Usage: ./configure [--help] [--prefix dir] [--bindir dir] [--datadir dir] ...

Options:

  General:
  --help                Print this help
  --qmakepath dir       qmake fullpath name
                        [example:  --qmakepath /usr/bin/qmake]

  --prefix dir          Installation prefix directory
                        [default:  /usr]
  --bindir dir          Executable installation directory
                        [default:  /usr/bin]
  --datadir dir         Data installation directory
                        [default:  /usr/share/bin/cb2bib]

  Unix/Linux only:
  --desktopdatadir dir  Desktop data installation directory
                        [default:  /usr/share/applications]
  --icondir dir         Icon installation directory
                        [default:  /usr/share/pixmaps]
  --disable_cbpoll      Disables clipboard poll

cliff@cliff-laptop:~/cb2bib-1.1.0$ make
make: *** No targets specified and no makefile found. Stop.

---

### Post by .Maleficus. on 2009-01-23
You were close - Add a space between --prefix and /usr/local and you should be good to go (you had --prefix/usr/local).  Run make and sudo make install again and it should be all set.

---

### Post by loobyloo on 2009-01-23
Thank you!
A couple of errors at the end...


cliff@cliff-laptop:~$ cd cb2bib-1.1.0/
cliff@cliff-laptop:~/cb2bib-1.1.0$ ./configure --prefix /usr/local

Configuration script for cb2Bib (Unix/Linux/MacOSX)

-----------------------------------------------------------------------
Platform: Linux
-----------------------------------------------------------------------
Setting installation directories...
Setting installation relative to dir: /usr/local
Setting installation executable to dir: /usr/local/bin
Setting installation cb2Bib data files relative to dir: /usr/local/share/cb2bib
Setting installation desktop data files to dir: /usr/local/share/applications
Setting installation icon file to dir: /usr/local/share/pixmaps
-----------------------------------------------------------------------

-----------------------------------------------------------------------
cb2Bib Info:
-----------------------------------------------------------------------
- This version requires Qt 4.3.0 or later
 
- Set the environment variable QTDIR if this script cannot determine
  the right Qt qmake
- QTDIR will only be used during configuration; it can later be reset
  to its original value
 
- Alternatively, set Qt 4.3 qmake's fullpath name with --qmakepath flag
-----------------------------------------------------------------------

Checking for Qt/qmake:
Environment variable QTDIR not set, checking elsewhere for qmake...
Checking for qmake tool... using /usr/bin/qmake
QMake version 2.01a
Using Qt version 4.4.3 in /usr/lib

Checking for additional tools:
Checking for make... using /usr/bin/make
Checking for kfmclient... not found
Checking for pdftotext... using /usr/bin/pdftotext
Checking for exiftool... not found

Setting clipboardPoll Enabled (Unix/Linux only)
Running /usr/bin/qmake -o Makefile
 
Configuration ended. Type 'make' and 'make install'.
cliff@cliff-laptop:~/cb2bib-1.1.0$ make
cd src/c2b/ && /usr/bin/qmake c2blib.pro -unix -o Makefile.c2blib
cd src/c2b/ && make -f Makefile.c2blib 
make[1]: Entering directory `/home/cliff/cb2bib-1.1.0/src/c2b'
g++ -c -pipe -O2 -fPIC -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. -I. -o approximatePattern.o approximatePattern.cpp
make[1]: g++: Command not found
make[1]: *** [approximatePattern.o] Error 127
make[1]: Leaving directory `/home/cliff/cb2bib-1.1.0/src/c2b'
make: *** [sub-src-c2b-c2blib-pro-make_default] Error 2

---

### Post by .Maleficus. on 2009-01-23
Looks like you don't have g++ installed.  Run 'sudo apt-get install build-essential' first and then the ./configure, make, sudo make install commands and *then* you should be set.

---

### Post by loobyloo on 2009-01-23
Great, nearly there.

It's generated yards of code and everything looks (??) OK.

Now when I try to run it from the alt+f2 thing, it just takes me to the folder and displays its contents.

There are two files in there called c2bib.  Clicking on wither of them produces "Details: Failed to execute child process "dl_cb2bib" (No such file or directory)"

---

### Post by mali2297 on 2009-01-23
Did you manage to run *sudo make install* without any errors?

If so, try just typing
```

c2bib

```
in a terminal window. Report any error messages.

---

### Post by loobyloo on 2009-01-23
Nope. Still not working: it looks like it's installing but fails at the very final stage:

cd cb2bib-1.1.0/
~/cb2bib-1.1.0$ write my dissertation for me now please
Command not found
:)

Thank you *very* much everyone for patience and assistance way beyond the call of duty. It's really appreciated. The next stage now will be to go through the instructions you all gave carefully and slowly so that I can absorb and understand what you've shown me.

In the short term though, I'd better start on the essay.

Best wishes

---

### Post by Tharmas on 2009-03-25
> **loobyloo said:**
> 
This disjunction between the willingness of others to help and the hours of frustration that moderately IT-literate people like myself have in trying to do something that would be simple in Windows illustrates the reasons why people don't bother with Linux.

Instead of whining, why don't you just install the binary?
It's linked from the Downloads section in the cb2bib home page. ([http://download.opensuse.org/repositories/home:/pereconstans/](http://download.opensuse.org/repositories/home:/pereconstans/))
[for Ubuntu 8.10 32 bits (i686) click here]("http://download.opensuse.org/repositories/home:/pereconstans/xUbuntu_8.10/i386/cb2bib_1.2.0_i386.deb")
You'll have the program installed with 2 clicks. 
I hope I can still help you.

---

### Post by 3rdalbum on 2009-03-25
Always look for a Debian package or a binary installer before going down the route of compiling the source code. Makes sense - after all, you always look for a binary installer on Windows first, and if you can't find one only then would you try and compile the source code.

Also, you do know that you can decompress .tar.gz files by double-clicking on them, don't you?

---

### Post by loobyloo on 2009-03-25
I can't remember how I did it now :)  But I installed something else from a tar.gz and as far as I can remember I think the (what? package manager?) installed it automatically, as you said, from a simple double click.  It's all a good learning experience though, even when you get a bit frustrated with it.

---

### Post by Tharmas on 2009-03-25
> **loobyloo said:**
> It's all a good learning experience though,
And in the end, it is fun to learn it and you can thank linux for it. I'm glad you didn't quit and manage to solve your problem. 
I just think the "Windows is easier, linux sucks" attitude is unfair.

About this package, I filed a bug asking for someone to package it in Ubuntu/universe:
[https://bugs.launchpad.net/bugs/348347](https://bugs.launchpad.net/bugs/348347)
lets hope we have some support.

---

### Post by cornsay on 2009-09-03
Hello, 

hope you don't mind me hijacking the thread with a similar query about cb2bib...

First up, the direct link to the binary about is dead, and the link to the index of the repository... well... I have to admit, I don't know what to do with that. The thing you can download looks the same as what you get from the cb2bib homepage. And it seems I may as well learn the long way round 

Instead, I've been trying to follow the instructions on the cb2bib installation page. I managed to get as far as the point where I type 'make' - and here's the output:

cd src/c2b/ && make -f Makefile.c2blib 
make[1]: Entering directory `/home/nick/cb2bib-1.3.2/src/c2b'
g++ -c -pipe -O2 -fPIC -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4 -I. -I. -o approximatePattern.o approximatePattern.cpp
In file included from approximatePattern.h:13,
                 from approximatePattern.cpp:10:
compositePattern.h:10:19: error: QRegExp: No such file or directory
compositePattern.h:11:23: error: QStringList: No such file or directory
In file included from approximatePattern.cpp:11:
cb2bib_utilities.h:10:16: error: QDir: No such file or directory
cb2bib_utilities.h:11:17: error: QFile: No such file or directory
cb2bib_utilities.h:12:21: error: QFileInfo: No such file or directory
cb2bib_utilities.h:14:19: error: QString: No such file or directory
cb2bib_utilities.h:15:19: error: QtDebug: No such file or directory
In file included from approximatePattern.h:13,
                 from approximatePattern.cpp:10:
compositePattern.h:18: error: expected ‘,’ or ‘...’ before ‘newPattern’
compositePattern.h:18: error: ISO C++ forbids declaration of ‘QString’ with no type
compositePattern.h:21: error: ‘QRegExp’ does not name a type
compositePattern.h:26: error: ISO C++ forbids declaration of ‘QList’ with no type
compositePattern.h:26: error: expected ‘;’ before ‘<’ token
compositePattern.h:32: error: expected `;' before ‘protected’
compositePattern.h:33: error: ISO C++ forbids declaration of ‘QList’ with no type
compositePattern.h:33: error: expected ‘;’ before ‘<’ token
compositePattern.h:34: error: ‘QRegExp’ does not name a type
compositePattern.h:35: error: ‘QString’ does not name a type
compositePattern.h:36: error: ‘QString’ does not name a type
compositePattern.h:37: error: ‘Qt’ has not been declared
compositePattern.h:37: error: ISO C++ forbids declaration of ‘CaseSensitivity’ with no type
compositePattern.h:37: error: expected ‘;’ before ‘caseSensitivity’
compositePattern.h:38: error: expected ‘,’ or ‘...’ before ‘&’ token
compositePattern.h:38: error: ISO C++ forbids declaration of ‘QString’ with no type
In file included from approximatePattern.cpp:10:
approximatePattern.h:20: error: expected ‘,’ or ‘...’ before ‘newPattern’
approximatePattern.h:20: error: ISO C++ forbids declaration of ‘QString’ with no type
approximatePattern.h:25: error: ISO C++ forbids declaration of ‘QList’ with no type
approximatePattern.h:25: error: expected ‘;’ before ‘<’ token
approximatePattern.h:26: error: ISO C++ forbids declaration of ‘QList’ with no type
approximatePattern.h:26: error: expected ‘;’ before ‘<’ token
approximatePattern.h:27: error: ‘QString’ does not name a type
approximatePattern.h:28: error: ‘QStringList’ does not name a type
approximatePattern.h:29: error: ‘QStringList’ does not name a type
approximatePattern.h:30: error: ‘QStringList’ does not name a type
approximatePattern.h:31: error: ‘QStringList’ does not name a type
approximatePattern.h:33: error: expected ‘,’ or ‘...’ before ‘&’ token
approximatePattern.h:33: error: ISO C++ forbids declaration of ‘QString’ with no type
approximatePattern.h:36: error: expected ‘,’ or ‘...’ before ‘&’ token
approximatePattern.h:36: error: ISO C++ forbids declaration of ‘QString’ with no type
In file included from approximatePattern.cpp:11:
cb2bib_utilities.h:26: error: ‘QString’ does not name a type
cb2bib_utilities.h:27: error: ‘QString’ does not name a type
cb2bib_utilities.h:28: error: expected initializer before ‘&’ token
cb2bib_utilities.h:29: error: expected initializer before ‘&’ token
cb2bib_utilities.h:31: error: ‘QRegExp’ does not name a type
cb2bib_utilities.h:37: error: ‘QRegExp’ does not name a type
cb2bib_utilities.h:38: error: ‘QRegExp’ does not name a type
cb2bib_utilities.h:39: error: ‘QRegExp’ does not name a type
cb2bib_utilities.h:40: error: ‘QRegExp’ does not name a type
cb2bib_utilities.h:41: error: ‘QStringMatcher’ does not name a type
cb2bib_utilities.h:42: error: ‘QStringMatcher’ does not name a type
cb2bib_utilities.h:46: error: ‘QString’ does not name a type
cb2bib_utilities.h:48: error: expected initializer before ‘&’ token
cb2bib_utilities.h:68: error: expected initializer before ‘&’ token
approximatePattern.cpp:239: error: expected `}' at end of input
make[1]: *** [approximatePattern.o] Error 1
make[1]: Leaving directory `/home/nick/cb2bib-1.3.2/src/c2b'
make: *** [sub-src-c2b-c2blib-pro-make_default] Error 2


What does all that mean, then? And what can I do to make it work?

Thanks very much.

---

### Post by perce on 2009-09-03
> **loobyloo said:**
> 
This disjunction between the willingness of others to help and the hours of frustration that moderately IT-literate people like myself have in trying to do something that would be simple in Windows illustrates the reasons why people don't bother with Linux.

Do you think compiling is so easy on Windows?

---

### Post by Tharmas on 2009-09-03
Cornsay,
Here are new links to you
[32 bit]("http://download.opensuse.org/repositories/home:/pereconstans/xUbuntu_9.04/i386/cb2bib_1.3.2_i386.deb")
[64 bit]("http://download.opensuse.org/repositories/home:/pereconstans/xUbuntu_9.04/amd64/cb2bib_1.3.2_amd64.deb")

Is that enough now?

---

### Post by perce on 2009-09-03
Get the deb from here: [http://http://download.opensuse.org/repositories/home:/pereconstans/xUbuntu_9.04/i386/]("http://download.opensuse.org/repositories/home:/pereconstans/xUbuntu_9.04/i386/") download it on your desktop, double click on it, and it will install. As easy as Windows...

---

### Post by Tharmas on 2009-09-03
> **perce said:**
> Get the deb from here: [http://http://download.opensuse.org/repositories/home:/pereconstans/xUbuntu_9.04/i386/]("http://download.opensuse.org/repositories/home:/pereconstans/xUbuntu_9.04/i386/") download it on your desktop, double click on it, and it will install. As easy as Windows...

Haha, I beat you to it by a couple of seconds...:D

---

### Post by cornsay on 2009-09-03
Thanks very much guys -- great to see you falling over each other to help me. And sorry for being so dumb -- I was (as you can see) looking in the right place, but didn't realise the i386 thing was what I wanted.

Well, I guess we never learn if we don't ask stupid questions once in a while. I'll know next time. Thanks again.

---

