---
title: "How to Install &quot;tar.gz&quot; on ubuntu....?"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Its_Rishi on 2011-02-13
i was founding many software packages in tar.gz for linux can i able to install that for my ubuntu 1. maverick...?

---

### Post by linuxsyst on 2011-02-13
tar.gz is an archive not an installation package,installation package is
.deb if your new you could install with the Debian package (.deb)

---

### Post by Vaphell on 2011-02-13
care to say what software packages you mean? have you checked if they exist in official repositories, where all you need to do is tick a checkbox and click 'Apply'?
Beginners shouldn't have to install apps manually unless there is no other way.

---

### Post by yeats on 2011-02-13
If possible, stick with what Ubuntu provides via the Software Center and Synaptic Package Manager.  However, if you're sure what you want to install is not available, read this:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Its_Rishi on 2011-02-13
> **yeats said:**
> If possible, stick with what Ubuntu provides via the Software Center and Synaptic Package Manager.  However, if you're sure what you want to install is not available, read this:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
After Installing the commands given in the link how to uninstall them by commands...?

---

### Post by shunan on 2011-02-13
think of it, I have never personal had the need but you could try checkinstall

[http://www.asic-linux.com.mx/~izto/checkinstall/](http://www.asic-linux.com.mx/~izto/checkinstall/)

---

### Post by yeats on 2011-02-13
[QUOTE=Its_Rishi]After Installing the commands given in the link how to uninstall them by commands...?[/QUOTE]

Usually, you can just do:

```
sudo make uninstall
```

but it depends on what it is.  Another good reason to stick to the repositories, or to downloaded .deb files until you're more experienced.

> think of it, I have never personal had the need but you could try checkinstall

checkinstall does work, in that it creates a deb on the fly, but it can be dangerous in that it will (potentially) rip out any dependencies it came with without regard for other programs that depend on them.

---

### Post by Its_Rishi on 2011-02-13
> **yeats said:**
> Usually, you can just do:

```
sudo make uninstall
```but it depends on what it is.  Another good reason to stick to the repositories, or to downloaded .deb files until you're more experienced.



checkinstall does work, in that it creates a deb on the fly, but it can be dangerous in that it will (potentially) rip out any dependencies it came with without regard for other programs that depend on them.
The uninstall command won't works...!

---

### Post by Its_Rishi on 2011-02-13
> sudo apt-get remove <package>
removed the packages what i installed from the command u given in the page link but after they removed the size of the packages won't freed...!

---

### Post by nrm88 on 2011-02-14
> **yeats said:**
> If possible, stick with what Ubuntu provides via the Software Center and Synaptic Package Manager.  However, if you're sure what you want to install is not available, read this:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
Thanks! Though most of the things i need i can find in the Software Center, i have been wanting to get qjoystick, so i can play flash games online with my game controller. But it has to be compiled, and i have no clue, yet. I've tried figuring it out, but im not very good with the terminal and commands yet :(

---

### Post by SexySara on 2011-02-14
I am new to linux also, I use Ubuntu 9.04 and I installed my first tarball the other day. I tend to learn better visually and these videos really helped me. Give them a go, I hope they work for you as they have for me. Watch both of them...

[http://www.youtube.com/watch?v=pjML-3Vs96c](http://www.youtube.com/watch?v=pjML-3Vs96c)
[http://www.youtube.com/watch?v=C_07phNne80](http://www.youtube.com/watch?v=C_07phNne80)

Enjoy!

---

### Post by DougieFresh4U on 2011-02-15
> **linuxsyst said:**
> tar.gz is an archive not an installation package,installation package is
.deb if your new you could install with the Debian package (.deb)

huh? :-k

---

### Post by SexySara on 2011-02-15
> **DougieFresh4U said:**
> huh? :-k In other words... installment packages are like Exe files in Windows, 2 clicks away and it installs. Much like Deb files, Windows exe's are the equivalent to a deb file and both are considered to be "installment packages" as it were.

The tar.gz files are compressed files with source and you must compile them and run them in terminal.

---

### Post by Guilden_NL on 2011-02-15
To clarify even further, a tarball just is a collection of two or more files together, no compression.  Just makes it easier to send them some place in one go.

It is usually used with compression, so the files are gathered together and compressed in a single TAR file.  In this case (the most common), it's a gzip compression.  Hence the tar.gz  This is just like a Winzip file in Windows.  It could be anything inside the thing.

TAR started as a means to back up files in a Tape ARchive, hence the name.

Sara is correct in that this file has source code that is not compiled, so you have to do that bit before installing it.

---

### Post by Its_Rishi on 2011-02-16
> **SexySara said:**
> In other words... installment packages are like Exe files in Windows, 2 clicks away and it installs. Much like Deb files, Windows exe's are the equivalent to a deb file and both are considered to be "installment packages" as it were.

The tar.gz files are compressed files with source and you must compile them and run them in terminal.

Well sara where can i find a good compiler for this type of file to install easily...?

---

### Post by bisban on 2011-02-16
> **nrm88 said:**
> Thanks! Though most of the things i need i can find in the Software Center, i have been wanting to get qjoystick, so i can play flash games online with my game controller. But it has to be compiled, and i have no clue, yet. I've tried figuring it out, but im not very good with the terminal and commands yet :(
 
So, does that mean the filename .tar.gz file when un-tarred ( tar -jxvf filenem.tar.gz) 
results into a folder containing source code files ( like files with dot-c or dot-cpp or dot-h) extensions. 
Then probably you need to first compile the sources for your distro.
 
Please google to search how to install a package from sources .
 
It normally has 3 steps.
1. Configure script to be run 
2. make 
3. make install 
 
Hope it helps.

---

### Post by lotharmat on 2011-02-16
> **Its_Rishi said:**
> Well sara where can i find a good compiler for this type of file to install easily...?

What language is it written in?

---

### Post by Its_Rishi on 2011-02-16
> **lotharmat said:**
> What language is it written in?

Well it is English...

---

### Post by cariboo on 2011-02-16
If you install the build-essentials meta-package from the repositories, it should install what you need to compile form source.

As a new user, I wouldn't advise installing from source unless you really need to, there are over 30,000 packages in the repositories, if you can't find what you need there, you may not need it.

The other thing to keep in mind, is that if you aren't getting the program from a trusted source, you may end up compromising your system.

---

### Post by sydbat on 2011-02-16
> **DougieFresh4U said:**
> huh? :-k

> **SexySara said:**
> In other words... installment packages are like Exe files in Windows, 2 clicks away and it installs. Much like Deb files, Windows exe's are the equivalent to a deb file and both are considered to be "installment packages" as it were.

The tar.gz files are compressed files with source and you must compile them and run them in terminal.[whispers]Sara, he was being sarcastic...[/whispers]

---

### Post by Its_Rishi on 2011-02-16
> **cariboo907 said:**
> If you install the build-essentials meta-package from the repositories, it should install what you need to compile form source.

As a new user, I wouldn't advise installing from source unless you really need to, there are over 30,000 packages in the repositories, if you can't find what you need there, you may not need it.

The other thing to keep in mind, is that if you aren't getting the program from a trusted source, you may end up compromising your system.
Then how would a new user (Beginner) know how to install or compile a different file format...?

---

### Post by oldos2er on 2011-02-16
> **Its_Rishi said:**
> Then how would a new user (Beginner) know how to install or compile a different file format...?

They would give the name of the program they're interested in, and a link to its website, so that others can take a look at it and advise them accordingly.

---

### Post by SexySara on 2011-02-16
> **sydbat said:**
> [whispers]Sara, he was being sarcastic...[/whispers]
  Sneaky sneaky :razz:

I use Jaunty and here is really good guide for future reference along with those Youtube links I posted... [http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Handling_.28Tar.2FGZip.29_and_.28Tar.2FBzip2.29_archives](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Handling_.28Tar.2FGZip.29_and_.28Tar.2FBzip2.29_archives)

---

### Post by DougieFresh4U on 2011-02-19
> **sydbat said:**
> [whispers]Sara, he was being sarcastic...[/whispers]

> **SexySara said:**
> Sneaky sneaky :razz:


I have always just thought of .tar and .bin etc. etc. as just another form of  'package' and I may have to jump through a few more hoops to install, in my 'round-about-way' ):P

---

