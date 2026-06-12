---
title: "installing a program"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by tbrownarcher on 2010-10-29
I have just installed ubuntu again.  a problem i have always had is how do i install a program And where does it go automaticly or manually?  I am trying to install wordbiz which is a program game for playing scrabble on the internet scrabble network (isc.ro)  when i download the file I have no clue where it goes nor how to invoke the installation and in the past i could not even find the file.  

could someone help me on the right path ???? 

this program requiers java virtual machine too .  How do i get that downloaded and how do i get that to work also. 

thanks,
Nate

---

### Post by Hippytaff on 2010-10-29
When you download stuff it should go (by default) to your Downloads folder.

Places > Downloads

or
```

cd /Downloads

```capital D :-)

Edit - Also...it might be worth upgrading to 10.04LTS or maybe even 10.10 - just an afterthought

---

### Post by sandyd on 2010-10-29
> **Hippytaff said:**
> When you download stuff it should go (by default) to your Downloads folder.

Places > Downloads

or
```

cd **~**/Downloads

```capital D :-)

Edit - Also...it might be worth upgrading to 10.04LTS or maybe even 10.10 - just an afterthought

Correction made.

---

### Post by tbrownarcher on 2010-10-29
Ok! I have been using 10.10 ver.  I do not know what LTS is. It says so in 'about ubuntu'. 

the program is in downloads, thanks,

Now what do i do with it to install ???? It wants 'Java Virtual Machine" for beginners so I have to install that .... then I need to install the Wordbiz program .. I don't know how to do this not even a clue.

This is the message I get when I double click the ***/home/nate/Downloads/jre-6u22-linux-i586(2).bin*** program which is in Downloads directory.  [B]"Could not display "/home/nate/Downloads/jre-6u22-linux-i586.bin".      
"The file is of an unknown type"
[/B]


Thanks,
Nate

---

### Post by Omnomnom on 2010-10-30
After you download and install this: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp) You double click on the .deb file and install as normal

---

### Post by tbrownarcher on 2010-10-30
> **Omnomnom said:**
> After you download and install this: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp) You double click on the .deb file and install as normal


installing is what' I need help with ... .

also that is a different program you are referencing ... does it contain the virtual machine???? 


thanks,
Nate

---

### Post by beew on 2010-10-30
Instead of downloading from the java site, I think it is better to install through Synaptic. 

Open up Synaptic, go to Settings > Repository > Other Software and click "add", then enter the following line to add the Canonical Partner repository
> deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner
Then close the dialogue box  and reload Synaptic.

 After that install the following packages from Synaptic: sun-java6-bin, sun-java6-jre, sun-java6-jdk and sun-java6-plugin. (jre is the java virtual machine)

Ubuntu uses open jdk as its default java, to switch to sun-java as the default, open a terminal and type

```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by tbrownarcher on 2010-10-30
""Open up Synaptic, go to Settings > Repository > Other Software and click "add", then enter the following line to add the Canonical Partner repository""

I do not know where to find 'Synaptic'

i don't understand the comment "Then close the dialogue box and **reload Synaptic**
Isn't Synaptic already running?


BTW!  I really appreciate the help!

Thanks,
Nate

---

### Post by Quackers on 2010-10-30
System > Administration > Synaptic Package Manager

---

### Post by beew on 2010-10-30
Synaptic is under System > Administration. It is kind of like the Software Center but has more options. I prefer using Synaptic to the Software Center (in fact I never use the SC)

Once you open up Synaptic, there is a menu bar on top. Go to "Settings", click it and choose "Repositories" from the drop down menu. On clicking "Repositories" another box would appear. Choose the tap "Other Software" for this box and click "Add" to add the line I told you to.  This adds the Canonical Partner repository to your sources list . You need to add this repository because sun-java is not in the default Ubuntu repository since Maverick (you used to be able to install sun-java by installing Ubuntu restricted extra)

After adding this line you close the box (the box with tabs from which you choose "Other Software")
Then you need to reload Synaptic so that the program manager is updated to the fact that a new repository has been added. To do this just click "Reload" at the upper left hand corner of the Synaptic window.

---

### Post by tbrownarcher on 2010-10-30
I can't seem to get the quote function here to work right so I'm manually quoting
BEEW here

[B]"After that install the following packages from Synaptic: sun-java6-bin, sun-java6-jre, sun-java6-jdk and sun-java6-plugin"
[/B]
Sun - java6-plugin is not in the list.  

I marked for install :  sun- java6-bin, sun- java6-jre, and sun- java6- jdk. 

the plugin one not being in the list here are the 3 that are : sun- java6- demo , sun- java6- javadb , and sun- java6- source.

Should i mark one of the 3 that is in the list?

thanks,
Nate

---

### Post by Quackers on 2010-10-30
All of them more likely. 
I don't know if it's what you want exactly but there is an open source Java6 runtime in the ubuntu-restricted-extras package, I believe.

---

### Post by tbrownarcher on 2010-10-30
Can't seem to use the quote function correctly so i'm manually quoting BEEW.


**"After that install the following packages from Synaptic: sun-java6-bin, sun-java6-jre, sun-java6-jdk and sun-java6-plugin"**


the sun-jaava6- plugin is not in the list .
What is in the list is 3 others called : sun-java6- demo, sun-java6- javadb, and sun- java6- source.  

is one of these 3 the one i should use or should i find it somewhere else?

thanks,
Nate

---

### Post by tbrownarcher on 2010-10-30
i'm having trouble with this site.  I can't reload it and get my last comment.  I'm clicking the submit replay so i don't know why i can't see my reply after i reload ?

so here is the last thing i said ... 

	
Re: installing a program
Can't seem to use the quote function correctly so i'm manually quoting BEEW.


**"After that install the following packages from Synaptic: sun-java6-bin, sun-java6-jre, sun-java6-jdk and sun-java6-plugin"**


the sun-jaava6- plugin is not in the list .
What is in the list is 3 others called : sun-java6- demo, sun-java6- javadb, and sun- java6- source.

is one of these 3 the one i should use or should i find it somewhere else?

thanks,
Nate

---

### Post by tbrownarcher on 2010-10-30
OH MY ! I'm sorry ..... I did not realize that we had gone to the second page .....***_[COLOR="black"][SIZE="4"] sigh ! [/SIZE][/COLOR]_***

thanks, 
Nate

---

### Post by Quackers on 2010-10-30
Did you see post #12?

---

### Post by tbrownarcher on 2010-10-30
QUACKERS: Yes i did ..... belatedly because i was fumbling with the pages i did mark all of them ........ 

so now they are all marked. BEEW said to type this line into the terminal.

sudo update-java-alternatives -s java-6-sun      I copied it and pasted it


This is the result of typing that into the terminal ... i copied and pasted it .... 


nate@nate:~$ sudo update-java-alternatives -s java-6-sun
[sudo] password for nate: 
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun
nate@nate:~$

---

### Post by tbrownarcher on 2010-10-30
maybe i got way ahead of things .. I don't know but ... I accepted all changes in synaptic for the java .  I can't find anything ... it took 2 min to complete but i just don't know where to look for whatever happened .... 

did it install the program 

thanks,
Nate

---

### Post by Quackers on 2010-10-30
Did you click on the green tick in the top bar? To apply your changes.

---

### Post by oneNF on 2010-10-30
This visual ref to installing with synaptic may be of help:
[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

Cheers

---

### Post by tbrownarcher on 2010-10-30
> **Quackers said:**
> Did you click on the green tick in the top bar? To apply your changes.

yes i did .  I still don't know where anything went 

thanks,
Nate

---

### Post by oldos2er on 2010-10-30
> **tbrownarcher said:**
> did it install the program

Installed programs show in Synaptic with a green box. To see where all the files in a package are installed to, right-click on an installed package, Properties, Installed Files.

---

### Post by tbrownarcher on 2010-10-30
i don't see a place that is a green box nor do i see a place that says installed programs or that says installed programs ... what am i doing wrong ???

thanks,
Nate

---

### Post by Quackers on 2010-10-30
Go into Synaptic and in the search box type the name of the package you installed. When it appears in the display right-click on it and select Properties and in the box that comes up go to the tab "Installed Files"

---

### Post by oldos2er on 2010-10-31
> **tbrownarcher said:**
> i don't see a place that is a green box nor do i see a place that says installed programs or that says installed programs ... what am i doing wrong ???


In Synaptic, click Status (in the lower left corner), in the upper left under 'All' there should be an entry 'Installed.'

---

### Post by tbrownarcher on 2010-10-31
OK! I'm sorry !  I seem to have no idea what i'm doing here in the way of installing.  Can we try this step by step?  

i was working with 2 files before and one got worked out automaticly on a reinstall.  The other, wordbiz did not get worked out. 


The file in question is wordbiz18linux.zip which is found at 

**_[SIZE="5"]http://isc.ro/linux/download.html[/SIZE]_**

I have downloaded the file into downloads.  From there I don't know what to do?  Since it's a zip do I unzip it?  How do I unzip it if I need to do so? Do I use synaptic somehow or do I need to do something else? or do I need start a new thread?

thanks, 
nate

---

### Post by oldos2er on 2010-10-31
Hm. I thought you were using Synaptic to check if Java was installed.

The instructions are "Unzip the archive. To run the program navigate to the wordbiz directory and type java -jar wordbiz.jar". Open a terminal, ```
cd Downloads/Wordbiz
java -jar wordbiz.jar
```

---

### Post by tbrownarcher on 2010-11-01
You are correct ... i started this because wordbiz required the virtual java machine and i was trying to get wordbiz to work ... since i started the Java side of the question was handled (i believe) by the additon of the updates at the end of the reinstall that i did.  So I don't need Jvm anymore.  

I'm sorry! i tried to relate that to everyone i guess i failed ... sigh

So now i'm trying to get into the wordbiz directory and this is what i got as a reply 

I tried 2 things neither succeeded .. i think it's because i need to be in a diffferent directory/folder.!

nate@home2:~$ cd Downloads/Wordbiz
bash: cd: Downloads/Wordbiz: No such file or directory
nate@home2:~$ cd Downloads/Wordbiz java -jar wordbiz.jar
bash: cd: Downloads/Wordbiz: No such file or directory
nate@home2:~$ 

Thanks,
Nate

---

### Post by tbrownarcher on 2010-11-01
I have another thread working among others on how to use the terminal

the wordbiz site says this for instructions to me to install i believe you read them but here they are.

    Download WordBiz 1.8 for Linux

    WordBiz is a Java program that allows you to play scrabble on ISC server using a graphical interface.
    To run WordBiz you will need to install Java Virtual Machine.

       1. CLICK HERE to download the zip archive.
       2. Unzip the archive.
       3. To run the program navigate to the wordbiz directory and type java -jar wordbiz.jar



nate@home2:~/Downloads/WordBiz$ wordbiz.jar
wordbiz.jar: command not found
nate@home2:~/Downloads/WordBiz$ 

Ok! I got it running ... the program (like all of them ) is instruction specific.  I'm guilt of not following instructions.  I typed wordbiz.jar when i was supposed to type java -jar wordbiz.jar

Wow i'm feeling small right now ...




it's up and running now and my next question is how do i get the Icon for the program associated with the program and placed on the desktop.  
and now i find that the program locks up the computer and no one is going to give me help on that ... all this and now i can't use it .....

thanks,
Nate

---

### Post by oldos2er on 2010-11-01
> **tbrownarcher said:**
> it's up and running now and my next question is how do i get the Icon for the program associated with the program and placed on the desktop.  
and now i find that the program locks up the computer and no one is going to give me help on that ... all this and now i can't use it 


 Do you have the java version known as OpenJDK, or Sun java installed? Some programs seem to prefer Sun's java; package name sun-java6-jre, and you must enable the partner repository first before installing it. Check in Synaptic, Settings, Repositories, Other Software tab, tick the boxes next to Canonical Partners and Canonical Partners (source code). Close the repositories window, then click Reload.

---

### Post by michellesuf on 2011-08-16
A friend loaded UBUNTU on my PC.  I have no idea how to use it.  I too, want to play Scrabble from isc.ro.  On Windows I never had a problem.  When I try to run the java jar I get an Error message that says it does not have a program to run it with.

I have been able to get the html scrabble board up. I cannot "connect" to the ISC Server.  That is what I am having problems with. 

I have Cannonical partners loaded on my system.  But, I have no idea what to do with it.

Please respond with step-by-step, as if I am the non-linux groupie I am, instructions.
Thanks.

---

### Post by oldos2er on 2011-08-16
The instructions to install java haven't really changed from what I wrote in post #30. If you have the partner repository enabled, open Synaptic, search for the package sun-java6-jre, and mark it for installation.

It might help to know which version of Ubuntu you're running.

---

