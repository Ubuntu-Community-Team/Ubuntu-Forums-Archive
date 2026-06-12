---
title: "Java : driving me crazy!"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by TBTS on 2010-03-06
Hi,
I am a shiny new linux user.
Everything fine until trying to get Java to run.
sudo install java worked fine: but is 6.15.
Downloaded a bin from sun, followed the chmod sudo routine and now have a bunch of crap sitting inside my home Downloads folder.

Can someone please let me know how to get that bin file to actually install itself so that it doesn't just decompress? I would like it to actually work...

---

### Post by kellemes on 2010-03-06
> **TBTS said:**
> Hi,
I am a shiny new linux user.
Everything fine until trying to get Java to run.
sudo install java worked fine: but is 6.15.
Downloaded a bin from sun, followed the chmod sudo routine and now have a bunch of crap sitting inside my home Downloads folder.

Can someone please let me know how to get that bin file to actually install itself so that it doesn't just decompress? I would like it to actually work...

From terminal-window and from location of filename.bin..
```
chmod +x filename.bin
./filename.bin
```

---

### Post by TBTS on 2010-03-06
thanks...

did that AGAIN, just to be sure it does nothing - NO DICE!

NO combos of chmod h+x, sudo this, shazzam that, will get this freaking sun bin to install: all that happens is it unpacks into local home folders and the system does not register it as a software or application install or whatever that's called on linux...

I'm starting to swear at my monitor here!

---

### Post by CoreyB. on 2010-03-06
What do you need a higher version for?

---

### Post by BigCajun on 2010-03-06
The .bin files from Sun are not "installers" the way you are thinking. All they do is extract to a directory. I use the latest versions myself and just extract it to a directory I chose (I use /usr/local/lib/java, but that's me).

In Ubuntu (and other distros I'm sure), they use "alternatives" to setup certain programs, like java. If you install Java from the repositories, it installs to some directory (can't recall exactly where at the moment) and then sets up links to it.

If you have the Ubuntu version installed, do a 'which java' and you'll see that java is at /usr/bin/java. But, if you do a long directory listing of /usr/bin/java, you'll see that it's just a symbolic link to /etc/alternatives/java. And, if you do a long listing of /etc/alternatives/java, you'll see that it's just another symbolic link to where it's really installed.

What you can do to use the version you downloaded from Sun is to:
1) explode it wherever you want. In your Downloads directory is fine, doesn't matter
2) Remove the /usr/bin/java link
3) Re-create the /usr/bin/java link to point to where you installed Java, specifically the java executable. Something like:

sudo ln -s /home/<your user id>/Downloads/jdk1.6.0_18/bin/java /usr/bin/java

You can also read up more on 'update-alternatives' and actually use that to officially setup java and replace the Ubuntu repo one with whatever one you download. This is not exactly a beginner topic though. My steps above isn't the best way to do it, but it will work for most things that need java.

If you also need to compile, then you can setup a link in /usr/bin to point to javac in the same way as step 3 above. Again, reading more on update-alternatives might lead you to a better solution.

The reason having a link in /usr/bin to java works is because, in most cases, /usr/bin is in your executable path (i.e. the PATH environment variable). You could also add the path where you installed java to you PATH variable, but you'd have to do it in such a way that it finds your Java install directory BEFORE the Ubuntu installed version. Again, not exactly a beginner topic.

Hope that helps a bit, sorry it's not more descriptive...

---

### Post by cacycleworks on 2010-03-06
I read the above and might add a hint or two.

In order to remove the /etc/alternatives or /usr/bin "links" you will need to use sudo. How I would typically do this is:

```
$cd /usr/bin
/usr/bin$ ls -al j*
-rwxr-xr-x 1 root root 14750 2009-11-10 01:18 java
/usr/bin$ sudo rm java
/usr/bin$ sudo ln -s ~/Downloads/...path.to.java.../java.bin java

```
I don't have java, just thought I'd share how to do what they said above.

---

### Post by TBTS on 2010-03-07
BigCajun and cacycleworks: thanks...

starting to get a feel for this stuff now. I really needed your post BigCajun because I was sure that this bin was just unpacking and hey: it is! Your post has helped me at least relax!

funny thing is that the bin doesn't even ask me where I want to unpack it - it just unloads directly where it is (no manners!).

Coming from windows a 'bin' file is usually executable in some fashion so I was thrown by the extension I think (I really was thinking that it was "installing" something).

Now this "linking (unlinking)" is complex. You are right about the "not a beginner topic" BigCajun. I have the {{path}} to the exploded files.

Now I need to:
cd /usr/bin
sudo rm java (removes the current Java link?)

then BigCajun and cacycleworks you guys have slightly different cmds (translating using {{path}}):
```
sudo ln -s {{path}}**/bin/java** /usr/bin/java
```
```
/usr/bin$ sudo ln -s {{path}}**/java.bin** java
```
now I realise that BigCajun has the /usr/bin/java as a parameter because I have not done the cd with his version so I need to specify the full path while cacycleworks has just java. But BigCajun has /bin/java where cacycleworks has java.bin.

what is the difference there and which should I use to add the correct link (which I assume the ln is).

then if I understand you right BigCajun, most execution like events that occur will find java because they see a link to java in the main executable path but this will not cover all things that execute and look for java (you mentioned compiling to javac). Now this is a little bit daunting...

---

### Post by AgentZ86 on 2010-03-07
Why do that when you can click on Applications/Ubuntu Software Center (type java) in the search field

And everything you can think of about java can install with one click ?

Java Start Web, and Browser Plugins etc etc etc.

And also in synaptic manager too search for java etc. and install

But with synaptic you have to know if your installing the right stuff but still simple enough too.

Anyhow, Hope this helps too.
:popcorn:

---

### Post by TBTS on 2010-03-07
see above: done that but only get an older version of java (6.15)

---

### Post by Norm24 on 2010-03-07
This worked for me:
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

---

### Post by BigCajun on 2010-03-07
> **TBTS said:**
> 

Now I need to:
cd /usr/bin
sudo rm java (removes the current Java link?)

Yep, that will remove the existing link.

> then BigCajun and cacycleworks you guys have slightly different cmds (translating using {{path}}):
```
sudo ln -s {{path}}**/bin/java** /usr/bin/java
```
```
/usr/bin$ sudo ln -s {{path}}**/java.bin** java
```
now I realise that BigCajun has the /usr/bin/java as a parameter because I have not done the cd with his version so I need to specify the full path while cacycleworks has just java. But BigCajun has /bin/java where cacycleworks has java.bin.

what is the difference there and which should I use to add the correct link (which I assume the ln is).

The command syntax is:
```
sudo ln -s <location_of_real_file> <location_of_link>
```
where the "location_of_real_file" is either the absolute or relative path to the file you want to link to, in this case the executable "java". The "location_of_link" is where you want the link to exists. The key part in this is that what you type in as the location of the real file. If it's NOT an absolute path, then it's HAS to be relative to the location of the link for it tow work. It's probably best to cd into the directory where you want the link to live, then just do something like this:
```
cd /usr/bin
sudo ln -s /home/tbts/Downloads/jdk1.6.0_18/bin/java .
```
The ".", since it is a directory and not a file, will cause the command to put the link in /usr/bin and give it the same name as the real file, in the above case, "java", fo a link of /usr/bin/java.

As for whether to use "java.bin" or "java", it depends on what the real file is and what you want the link to be. Most programs are going to look for an executable named "java", so you want the second part of the link to be "java". The first part should also be "java" (instead of "java.bin) because when you extract the .bin, look in the directory where you extract it. Let's say you extract it inside /home/tbts/Downloads. After extracting, you should have a directory at /home/tbts/Downloads/jdk1.6.0_18 if you got the latest JDK from sun. Inside that directory will be a bin directory (/home/tbts/Downloads/jdk1.6.0_18/bin). And inside that directory is most of the Java executables like "java", "javac", "keytool", etc. For each one of these that you want to be able to use, you will need to create a symbolic link. The "-s" part of the command makes the link a symbolic link when you create it (as opposed to a hard link).

> then if I understand you right BigCajun, most execution like events that occur will find java because they see a link to java in the main executable path but this will not cover all things that execute and look for java (you mentioned compiling to javac). Now this is a little bit daunting...

This is true. If you want a complete java install and make it seamless, then you will have to follow one of a few approaches. Here are 2:

- Add a symbolic link for EVERYTHING you want to use in /usr/bin
OR
- install Java from the repositories and take a look at /var/lib/dpkg/alternatives/

The first method is trivial, but time consuming to set them all up. The biggest downside to that method is that if you want to upgrade again later, you'll have to remove all the links and redo them with the new locations (say jdk1.6.0_19 if that comes out).

The second method is "better" in that it follows the "akternatives" stuff I was talking about in my first post. But it's less trivial and more time consuming. If you look at that directory, you'll see a bunch of text files that match up with just about everything that you can run when you install a JDK. Each of the files has information about where ALL of the programs that provide java, javac, keytool, etc. are, and what priority they should have. These files are what's used to create the links in /etc/alternatives.

One more thing you might want to do if you plan to keep up with the latest JDKs is to create yet another level of indirection when you first set this up. This way, you go through the time consuming part once, and then everyt time you upgrade your JDK, you only have to modify 1 link.

Let's say you extract JDK 1.6.0_18 to /home/tbts/Downloads. Instead of setting all your links to point there, first create a link to that directory, like this:
```
cd /home/tbts/Downloads
ln -s jdk1.6.0_18 jdk1.6
```
This will create a link, /home/tbts/Downloads/jdk1.6 that points to you _18 JDK. Now set all of the /usr/bin links up to point to /home/tbts/Downloads/jdk1.6 like this:
```
cd /usr/bin
sudo ln -s /home/tbts/Downloads/jdk1.6/bin/java .
```
etc.
Now, if you download a newer (or older) JDK, all you have to do is remove the link in /home/tbts/Downloads, and re-link it to the new directory like this:
```
cd /home/tbts/Dwonloads
rm ./jdk1.6
ln -s jdk1.6.0_19 jdk1.6
```
And instantly all your links in /usr/bin are updated!

Sorry for such a long post. Hope it helps a little more.

---

### Post by BigCajun on 2010-03-07
> **Norm24 said:**
> This worked for me:
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

Man, I got so into my post above that I didn't even think to go looking for something like this. I haven't looked at it totally, but it's probably more thourough than my method.

---

### Post by Sef on 2010-03-07
Actually it is much easier to download it from the Ubuntu Software Center.  In Search type in either: sun java or openjdk.   The latter is the open source version of Java.  

Update: Just make sure that the universe and multiverse repositories are ticked.  (In Ubuntu Software Center: Edit > Software Sources)

---

### Post by Norm24 on 2010-03-07
> **BigCajun said:**
> Man, I got so into my post above that I didn't even think to go looking for something like this. I haven't looked at it totally, but it's probably more thourough than my method.

I hadn't thought about java in awhile until I saw this thread.I just used it to update to 18.

---

