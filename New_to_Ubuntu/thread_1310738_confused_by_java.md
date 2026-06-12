---
title: "confused by java"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by johnyjj2 on 2009-11-02
Hello :-)!

I installed this: JDK 6 Update 16 with NetBeans 6.7.1 from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

I include with this post (as txt) result of the following:

```
java -version

/usr/lib/jvm/java-1.5.0-sun/jre/bin/java -version
ls -la /usr/lib/jvm/java-1.5.0-sun/jre/bin

whereis java
```

Basically I've got problem with using java:

```
mainacc@mainacc-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/bin$ java -mx256m -jar bin/HelloWorld.jar
The program 'java' can be found in the following packages:
* gcj-4.4-jre-headless
* openjdk-6-jre-headless
* cacao
* gij-4.3
* jamvm
* kaffe
Try: sudo apt-get install <selected package>
java: command not found
mainacc@mainacc-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/bin$ sudo apt-get install gcj-4.4-jre-headless
[sudo] password for mainacc:
Czytanie list pakiet&#258;&#322;w... Gotowe
Budowanie drzewa zale&#313;&#317;no&#313;›ci
Odczyt informacji o stanie... Gotowe
E: Nie uda&#313;‚o siÄ™ odnale&#313;&#351;Ä‡ pakietu gcj-4.4-jre-headless
mainacc@mainacc-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3/bin$
```

In other words I have file HelloWorld.jar and I try to open it with "java -mx256m -jar bin/HelloWorld.jar" (as explained in the tutorial) but it doesn't run it. So I did what it suggested me to do, i.e. "sudo apt-get install gcj-4.4-jre-headless" but it says "Packet gcj-4.4-jre-headless cannot be found".

Greetings:)!

---

### Post by Mighty_Joe on 2009-11-02
> **johnyjj2 said:**
> I installed this: JDK 6 Update 16 with NetBeans 6.7.1 from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

If you install Java yourself rather than relying on what is in Ubuntu's repository, you have to set up the environment yourself as well.  
If you want to do it Ubuntu's way, see [here]("https://help.ubuntu.com/community/JavaInstallation") and [here]("https://help.ubuntu.com/community/Java").  I recommend using Sun Java.  The [GCJ]("http://gcc.gnu.org/java/") that you installed via apt-get is slow and buggy.

---

### Post by johnyjj2 on 2009-11-02
Thanks for your answer :-)!

I tried the following:
```
myacc@myacc-laptop:~$ echo "export PATH=\$PATH:/usr/local/jdk1.6.0_16/bin" >> ~/.bashrc
myacc@myacc-laptop:~$ . ~/.bashrc
```
And I've got other errors with executing HelloWorld.jar of CMU Sphinx:
```
mainacc@mainacc-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3$ java -mx256m -jar bin/HelloWorld.jar
Exception in thread "main" java.lang.NoClassDefFoundError: javax/speech/recognition/GrammarException
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:169)
    at edu.cmu.sphinx.util.props.ConfigurationManager.getPropertySheet(ConfigurationManager.java:89)
    at edu.cmu.sphinx.util.props.PropertySheet.getComponent(PropertySheet.java:278)
    at edu.cmu.sphinx.linguist.flat.FlatLinguist.newProperties(FlatLinguist.java:173)
    at edu.cmu.sphinx.util.props.PropertySheet.getOwner(PropertySheet.java:430)
    at edu.cmu.sphinx.util.props.PropertySheet.getComponent(PropertySheet.java:280)
    at edu.cmu.sphinx.decoder.search.SimpleBreadthFirstSearchManager.newProperties(SimpleBreadthFirstSearchManager.java:145)
    at edu.cmu.sphinx.util.props.PropertySheet.getOwner(PropertySheet.java:430)
    at edu.cmu.sphinx.util.props.PropertySheet.getComponent(PropertySheet.java:280)
    at edu.cmu.sphinx.decoder.AbstractDecoder.newProperties(AbstractDecoder.java:52)
    at edu.cmu.sphinx.decoder.Decoder.newProperties(Decoder.java:31)
    at edu.cmu.sphinx.util.props.PropertySheet.getOwner(PropertySheet.java:430)
    at edu.cmu.sphinx.util.props.PropertySheet.getComponent(PropertySheet.java:280)
    at edu.cmu.sphinx.recognizer.Recognizer.newProperties(Recognizer.java:78)
    at edu.cmu.sphinx.util.props.PropertySheet.getOwner(PropertySheet.java:430)
    at edu.cmu.sphinx.util.props.ConfigurationManager.lookup(ConfigurationManager.java:163)
    at edu.cmu.sphinx.demo.helloworld.HelloWorld.main(HelloWorld.java:36)
Caused by: java.lang.ClassNotFoundException: javax.speech.recognition.GrammarException
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 18 more
mainacc@mainacc-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3$
```
(To avoid crossposting, let me give link to CMU Sphinx forum -> [https://sourceforge.net/projects/cmusphinx/forums/forum/5471/topic/3445960/index/page/1](https://sourceforge.net/projects/cmusphinx/forums/forum/5471/topic/3445960/index/page/1))

It looks like it is problem rather with CMU Sphinx, then with Java configuration. However, do I still need to follow what is in those links given to me in the previous post? Or is it the problem of CMU Sphinx, not connected with my Java configuration?

Greetings :-)!

---

### Post by Mighty_Joe on 2009-11-02
```

Exception in thread "main" java.lang.NoClassDefFoundError: javax/speech/recognition/GrammarException

```

GrammarException isn't in the Java API. Apparently it's from [this project (FreeTTS)]("http://sourceforge.net/projects/freetts/files/"), so I would assume that the problem is with Sphinx.
Look in your the directory you unzipped the Sphinx download. There's a doc/jsapi_setup.html document that explains how to install the JSAPI.  Apparently it uses a different license from Sphinx, so they can't directly include it.

---

### Post by johnyjj2 on 2009-11-02
Thanks for answer :-)!

However, **I followed that short jsapi_setup.html previously. After your suggestion, I repeated the same once again but it still doesn't help - there are the same errors.** I guess the easiest way can be simply to install other Linux than Ubuntu, which has got minimum requirements of installing anything to have Java running properly. (Which distribution of Linux)? By the way, are you somehow involved in using or designing CMU Sphinx :-)?

Greetings!
  
PS Previously I tried to compile everything and execute those perl scripts in Windows but there were so many problems that after switching to Linux, I finished the whole task much faster. However, installing CMU Sphinx wasn't enough - now I need to execute HelloWorld.jar and there are other problems like those explained above :-P.

PS2 Would installing TTS 1.2 would be a good solution to my problem? (Probably not, because there was nothing about installing freetts here: [http://www.speech.cs.cmu.edu/sphinx/tutorial.html](http://www.speech.cs.cmu.edu/sphinx/tutorial.html) and here: [http://cmusphinx.sourceforge.net/sphinx4/#download_and_install](http://cmusphinx.sourceforge.net/sphinx4/#download_and_install)). From here file:///home/mainacc/tutorial/freetts-1.2.2-bin/freetts-1.2/docs/index.html#download_and_install I understand that adding  lib/freetts.jar to classpath is the only one thing which I need to install freetts (of course after unpacking it).
I also found this: [http://java.sun.com/products/java-media/speech/forDevelopers/jsapi-doc/javax/speech/recognition/GrammarException.html](http://java.sun.com/products/java-media/speech/forDevelopers/jsapi-doc/javax/speech/recognition/GrammarException.html) but it doesn't help me.

---

### Post by johnyjj2 on 2009-11-02
Can anybody help me, please?

Summing up, this problem:

```
mainacc@mainacc-laptop:~/tutorial/sphinx4-1.0beta3-bin/sphinx4-1.0beta3$ java -mx256m -jar bin/HelloWorld.jar
Exception in thread "main" java.lang.NoClassDefFoundError: javax/speech/recognition/GrammarException
```

couldn't be solved by applying this
[http://freetts.sourceforge.net/docs/jsapi_setup.html](http://freetts.sourceforge.net/docs/jsapi_setup.html)

```
 *  Go to the lib directory.
* Type chmod +x ./jsapi.sh.
* Type sh ./jsapi.sh and view the BCL.
* If the BCL is acceptable, accept it by typing "y". The jsapi.jar file will be unpacked and deposited into the lib directory. 
```

Thanks for help in advance :-)!
Greetings :-)!

---

### Post by Mighty_Joe on 2009-11-02
> **johnyjj2 said:**
> Can anybody help me, please?


Please be patient.  Bumping your own post after less than an hour is considered rude.
I just tried running Sphinx and it ran fine after running the jsapi script.  Look in your sphinx4-1.0beta3/lib directory for a jsapi.jar file.

---

### Post by johnyjj2 on 2009-11-02
OK, from now I would be waiting at least one hour :-). I just got confused that each my post is lost after several minutes because I have never seen this crowded forum :-P. Thanks :)

Now I see what is wrong. The following is shown after choosing 'y' to accept the licence:
```
./jsapi.sh: 1428: uudecode: not found
restore of jsapi.jar failed
jsapi.jar: MD5 check failed
```
Where to get this jsapi.jar from?

Greetings:)!

---

### Post by Mighty_Joe on 2009-11-02
> **johnyjj2 said:**
> OK, from now I would be waiting at least one hour :-). I just got confused that each my post is lost after several minutes because I have never seen this crowded forum :-P. Thanks :)

So did you look in your sphinx4-1.0beta3/lib directory for a jsapi.jar file?

---

### Post by johnyjj2 on 2009-11-02
Yes, I looked. There is no such a file. I executed sh once again and I see (after choosing 'y') to accept the licence:

```
./jsapi.sh: 1428: uudecode: not found
restore of jsapi.jar failed
jsapi.jar: MD5 check failed
```

Where to get this jsapi.jar from?

Greetings:)!

---

### Post by Mighty_Joe on 2009-11-02
> **johnyjj2 said:**
> 
```
./jsapi.sh: 1428: uudecode: not found
restore of jsapi.jar failed
jsapi.jar: MD5 check failed
```


You may want to try installing the sharutils package.  That's where the uudecode program is found.

---

### Post by johnyjj2 on 2009-11-02
Thanks!

I'm going to install it for a moment. (I followed ordinary, standard installation of Ubuntu 9.10 so why do you have it and I don't?).

Just now I tried to install PocketSphinx. It said me that I need to install SphinxBase at first. So I install SphinxBase. I executed ./configure, make, make check and there is error with make install:

```
mainacc@mainacc-laptop:~/tutorial/sphinxbase$ make install
Making install in src
make[1]: Entering directory `/home/mainacc/tutorial/sphinxbase/src'
Making install in libsphinxbase
make[2]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase'
Making install in util
make[3]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/util'
make[4]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/util'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/util'
make[3]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/util'
Making install in fe
make[3]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/fe'
make[4]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/fe'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/fe'
make[3]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/fe'
Making install in feat
make[3]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/feat'
make[4]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/feat'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/feat'
make[3]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/feat'
Making install in lm
make[3]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/lm'
make  install-am
make[4]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/lm'
make[5]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/lm'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/lm'
make[4]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/lm'
make[3]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase/lm'
make[3]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase'
make[4]: Entering directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libsphinxbase.la' '/usr/local/lib/libsphinxbase.la'
/usr/bin/install -c .libs/libsphinxbase.so.1.0.0 /usr/local/lib/libsphinxbase.so.1.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libsphinxbase.so.1.0.0': Permission denied
make[4]: *** [install-libLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src/libsphinxbase'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mainacc/tutorial/sphinxbase/src'
make: *** [install-recursive] Error 1
mainacc@mainacc-laptop:~/tutorial/sphinxbase$ ^C
mainacc@mainacc-laptop:~/tutorial/sphinxbase$ 
```

As I see it cannot create /usr/local/lib/libsphinxbase.so.1.0.0 because permission is denied. I'm rather newbie to Linux :) (but I'm gonna change it soon :P). Do I simply need to change privilidges to that file by "sudo chmod"?

Greetings:)!

---

### Post by Mighty_Joe on 2009-11-02
> **johnyjj2 said:**
> I'm going to install it for a moment. (I followed ordinary, standard installation of Ubuntu 9.10 so why do you have it and I don't?).

I'm running CrunchBang 9.04, so either it includes it or something else I installed has it as a dependency.  
As for SphinxBase, you should probably do a "sudo make install", but really, we should focus on a single problem.  I'm beginning to get the feeling that you are grasping at straws instead of systematically trying to fix problems.

---

### Post by johnyjj2 on 2009-11-02
Thanks for help once more :-)

I would say it is rather lack of experience in Linux and being used to Windows. In Win I don't have to use any sudo because I always use account with admin privilidges. And in other distributions of Linux I always did "su" before installing anything, here it looks like I need to use sudo before any action which requires admin privilidges.

I also tried to read the whole tutorial before installing it and follow each step. I followed that one with running jsapi.sh as well. However, I didn't pay enough much attention to the output, I assumed everything was OK. And the output which said about GrammarException didn't say anything to me. I looked for it in google and found one page which was for programmers to take advantage of this exception.

I guess I need some more knowledge about all of those Java-connected things which are to be installed and configured in Linux/Windows because I got lost in all those files, privilidges, configuration, dependencies and so on. In general I'd like to do something more difficult, i.e. install PocketSphinx in Ubuntu, try those examplary applications in Ubuntu and later copy one of those examplary applications to the mobile phone to check whether it can be executed on embedded device. Later to modify those examples, just by analysing the code of examplary applications. So if you can give me some hints (preferably by giving links to proper tutorials) I would be greatful and there won't be need to post questions about minor issues and problems.

Summing up, what I need to know about is all of those files, configuration and so on which must be fulfilled to run examplary applications (so that I can check what I've got and what I need on both Ubuntu and mobile phone and install/configure what is needed). It includes both Java-connected and PocketSphinx-connected files, configuration and so on.

Greetings :-)!

PS I installed SphinxBase correctly. Now I do:
```
mainacc@mainacc-laptop:~/tutorial/pocketsphinx-0.5.1$ ./configure
```
and it works. So I do:
```
 mainacc@mainacc-laptop:~/tutorial/pocketsphinx-0.5.1$ sudo make
```
And I've got errors:
```
 pocketsphinx.c:3282: warning: implicit declaration of function ‘Py_XDECREF’
error: command 'gcc' failed with exit status 1
make[1]: *** [pymod-build-stamp] Error 1
make[1]: Leaving directory `/home/mainacc/tutorial/pocketsphinx-0.5.1/python'
make: *** [all-recursive] Error 1
```
I googled for "error: command 'gcc' failed with exit status 1". I tried one of those suggestion and executed "./make" instead of "make" but it didn't help. I guess here ([http://mail.python.org/pipermail/pythonmac-sig/2004-May/011066.html](http://mail.python.org/pipermail/pythonmac-sig/2004-May/011066.html)) may be solution. It says about improper gcc. I followed those commands (maybe they would say something to you because they are no help for me):
```
mainacc@mainacc-laptop:~/tutorial/pocketsphinx-0.5.1$ gcc --version
gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

mainacc@mainacc-laptop:~/tutorial/pocketsphinx-0.5.1$ gcc -no-cpp-precmp
gcc: unrecognized option '-no-cpp-precmp'
gcc: no input files
mainacc@mainacc-laptop:~/tutorial/pocketsphinx-0.5.1$ 
```

Greetings:)

---

### Post by johnyjj2 on 2009-11-02
Please, help me with getting rid of "**error: command 'gcc' failed with exit status 1**". Thanks in advance :)!

---

### Post by Mighty_Joe on 2009-11-03
I don't know why you are trying to compile pocketsphinx when I've already demonstrated that the Sphinx HelloWorld can be run if you can get jsapi.jar extracted.  
Ill make it easy on you.  Try downloading the attached file, unzip it and put it in the sphinx4-1.0beta3/lib directory (I presume that you agree to the licensing of this file).

---

### Post by aextance on 2010-01-06
I had a similar problem to johnyjj2 when trying to install sphinx, which stemmed from not having sharutils when installing jsapi.jar. I just installed sharutils from Synaptic, and I was away. So, thanks Mighty_Joe for tackling this issue.

I'm not a hardcore programmer, so I'm pretty daunted by the complexity of Sphinx at this point. You have my sympathy johny jj2.

---

