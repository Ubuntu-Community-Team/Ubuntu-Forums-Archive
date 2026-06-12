---
title: "cockatrice"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by joshcanfield on 2011-06-19
im trying to install cockatrice to play mtg on my computer. I am having trouble installing it. i have gone to cockatrice.de and downloaded the source code then i get stuck from there. is there any body that can help me?

I have downloaded the source to my homefolder, opened terminal, and typed sudo apt-get install cockatrice. and it says unable to locate package cockatrice. 
Did I do the install wrong?

---

### Post by wolfen69 on 2011-06-19
When you do:
```
sudo apt-get install any_application
```
you are trying to get an app from servers very far away via downloading. And then it would install automatically. That is not how you install apps you have downloaded to your computer.

In your case, it is probably a tar.gz file or something of that nature. You need to extract it first by right clicking it and select "extract here". Then open it, and there might be a README file in there to explain how to install it. If you do not understand it, copy and paste the readme me here, and we will help.

---

### Post by joshcanfield on 2011-06-19
aaahhh. i see wont make that mistake again. ok so far i have downloaded, extracted and I cant find installation instructions any where in the files. also it is a tar.gz file

---

### Post by kaldor on 2011-06-19
> **joshcanfield said:**
> aaahhh. i see wont make that mistake again. ok so far i have downloaded, extracted and I cant find installation instructions any where in the files. also it is a tar.gz file

Annoying that they only give out the Source Code :(

I just downloaded it myself just to take a look. Here's what you should do.

[LIST]
[*]Saved it to my *Downloads* folder
[*]Right click > Extract Here
[*]Entered the folder it created, called "*cockatrice-20110309*"
[/LIST]

That's where I assume you are now. I then looked in the source and did some searching, because they seem to have a non-standard method of installing it. You'll need the Terminal for this bit. If you're on the new Unity interface, press the Ubuntu button and type "Terminal". If you're on the classic (two panel UI) go to "Applications > Accessories > Terminal".

In the terminal, "cd" into the directory you extracted it in. For example, if you did this in your Downloads folder, run the command shown here: ```
cd Downloads/cockatrice*
```

*Edit: Apparently you may need the qt4 development tools for this to work. Run "sudo apt-get install libqt4-dev" and you should be good to go.*

Then, you should follow the instructions that I copy/pasted from the Cockatrice forums. I am assuming you are now in the "cockatrice-20110309" directory. Run the following two commands.

```
cd cockatrice

lrelease translations/*.ts && qmake && make
```

After that's done,

```
cd ../oracle

qmake && make
```


Stolen from their forums:
> The compiled executables are located cockatrice/cockatrice/cockatrice and cockatrice/oracle/oracle, respectively. Execute them there or copy them in ~/bin or /usr/local/bin or wherever you like.

They deem the release stable. They really should have packaged it :(

---

### Post by joshcanfield on 2011-06-19
ok that helped and it started to work till i ran in to a g++ problem....this is averything i did

scott@scott-Aspire-M1610:~$ cd Downloads/cockatrice*
scott@scott-Aspire-M1610:~/Downloads/cockatrice-20110309$ cd cockatrice
scott@scott-Aspire-M1610:~/Downloads/cockatrice-20110309/cockatrice$ lrelease translations/*.ts && qmake && make
Updating 'translations/cockatrice_de.qm'...
    Generated 567 translation(s) (567 finished and 0 unfinished)
Updating 'translations/cockatrice_en.qm'...
    Generated 4 translation(s) (4 finished and 0 unfinished)
    Ignored 563 untranslated source text(s)
Updating 'translations/cockatrice_es.qm'...
    Generated 567 translation(s) (567 finished and 0 unfinished)
Updating 'translations/cockatrice_fr.qm'...
    Generated 567 translation(s) (567 finished and 0 unfinished)
Updating 'translations/cockatrice_ja.qm'...
    Generated 567 translation(s) (567 finished and 0 unfinished)
Updating 'translations/cockatrice_pt-br.qm'...
    Generated 567 translation(s) (567 finished and 0 unfinished)
Updating 'translations/cockatrice_pt.qm'...
    Generated 567 translation(s) (567 finished and 0 unfinished)
Updating 'translations/cockatrice_ru.qm'...
    Generated 567 translation(s) (567 finished and 0 unfinished)
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/abstractcounter.o src/abstractcounter.cpp
make: g++: Command not found
make: *** [build/abstractcounter.o] Error 127


also I did installed the qlibqt4-dev before all these steps just to be sure

---

### Post by kaldor on 2011-06-19
> **joshcanfield said:**
> ok that helped and it started to work till i ran in to a g++ problem....this is averything i did

Ah, so let's try installing the Build Essential package. That should have everything you'd need:

```
sudo apt-get install build-essential
```

Once that's installed, start rebuilding the code again. No need to start over; just run the lrelease bit again.

---

### Post by joshcanfield on 2011-06-20
ok so i did all that and looks like everything went fine...except, where is it now? i cant find it on on the computer

I have done the oracle data base and when i click on cockatrice it brings the path set up. where should i direct my paths to?

---

### Post by kaldor on 2011-06-20
I am not sure how to configure the program itself. I'd suggest asking in their forums ([www.cockatrice.de](www.cockatrice.de)) for that. 

The program should have made a cockatrice binary/executable file in the cockatrice folder somewhere.

---

### Post by joshcanfield on 2011-06-24
I tried to put cockatrice on my bros comp and it gave this 

jonathan@jonathan-DW236A-ABA-a545c:~/Downloads/cockatrice-20110309/cockatrice$  lrelease translations/*.ts && qmake && make
g++ -c  -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT  -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.  -Isrc -I../common -I/usr/include/qt3 -Ibuild/ -o  build/abstractcounter.o src/abstractcounter.cpp
In file included from src/abstractcounter.cpp:1:0:
src/abstractcounter.h:4:25: fatal error: QGraphicsItem: No such file or directory
compilation terminated.
make: *** [build/abstractcounter.o] Error 1

edit...
i dont know what this message is asking
...i dried to search anything about qgraphics, and found nothing can anybody tell me what to tell my bro about what he needs to complete cockatrice,
i would love to be aboe to play against him using cockatrice

---

### Post by Cerberize on 2012-07-29
First install the build-tools
```
$ sudo apt-get install build-essential
```Then the following commands
```
$ sudo apt-get install libqt4-dev qtmobility-dev 
$ git clone git://cockatrice.git.sourceforge.net/gitroot/cockatrice/cockatrice 
$ cd cockatrice/cockatrice 
$ lrelease cockatrice.pro 
$ qmake && make 
$ cd ../oracle $ qmake && make

```

Succesfully tested on july, 29

---

