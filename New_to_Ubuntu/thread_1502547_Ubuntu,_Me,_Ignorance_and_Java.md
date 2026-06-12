---
title: "Ubuntu, Me, Ignorance and Java"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by tomnewton on 2010-06-05
Hi there,

(For the short version, skip to the non-italic part)

[I]I installed ubuntu Karmic Koala Netbook Remix on my very old laptop after accidentally destroying XP (but it was frustrating so I don't mind). After successfully setting up my wireless Internet connection, I was flushed with my first success. It told me to update to version 10.04, so I did so. I rebooted the system after my machine had completed its period of ascension.

I loaded Miniclip on Firefox and clicked on my favourite game. Lo and behold, Java was not installed on my machine. 'No matter' I said to myself confidently, and I swiftly downloaded Java version 6u20 for Ubuntu Linux. After about 20 seconds it had finished its migration to my laptop, and I double clicked the file in the downloads window.

This was my first hurdle; it asked me to choose an application to run the executable file with.

My first thought was a commonly used phrase on online games; 'wtf?'. I closed the box and Googled how to install Java for Linux. What I got back from the official installation instructions was a load of gibberish. It assumed I possessed a fluent knowledge of Ubuntish.

After several hours of trawling through guides and tutorials on the Internet, several of which were on these very forums, and several threads from these forums that were revealed to me with a few searches, nothing made any sense (although I am sure this was more to do with my own stupidity rather than a lack of quality in the guides). I was no closer to installing Java than I was four hours ago.

So I here I am, asking, nay, begging for help in installing Java, and other essential programs. Hopefully, some kind person (or people) will have pointed me in the direction of (or left) some [/I]very* basic instructions on installing Java for the very ignorant and long time Windows XP user by the morning when I come back to my computer screen with a fresh mind (so I may be more able to learn Ubuntish)*.[I] Please assume I know nothing about PCs, Linux, Ubuntu. I do however, know basic Terminal commands, such as cp, mv, rv, cd.

To those who offer a portion of their knowledge, I thank them with the most heartfelt of thanks.

[/I]Basically, to cut a long story short, I need to install Java on my Ubuntu v 10.04, and know next to nothing. I tried and failed to install it. I tried and failed to get help from guides, and found both those and threads that came up in my search of these forums for Java help confusing.

Please help me.  ; (

Thanks, Tom.

---

### Post by fatality_uk on 2010-06-05
This should provide Java for you.
[http://wojox.homelinux.org/?p=78](http://wojox.homelinux.org/?p=78)

---

### Post by acrazyplayer on 2010-06-05
Okay if you downloaded this file [http://javadl.sun.com/webapps/download/AutoDL?BundleId=39485](http://javadl.sun.com/webapps/download/AutoDL?BundleId=39485)
then what you have to do is simple. go to where you downloaded it and right click on it, go to "properties" and then go to "permissions" you will notice a checkbox that has the word "execute" next to it. check it.

Now open up a terminal and drag and drop the file you just made executable into the terminal, hit the "home" button on the keyboard and type in "sudo" then  space and hit enter.

After everything is done then try the site again. You may need to do other steps. 

If you want to skip all this and use a different type of java that works the same then simply type into a terminal "sudo apt-get install ubuntu-restricted-extras"

---

### Post by Autodave on 2010-06-05
> **tomnewton said:**
> Hi there,

(For the short version, skip to the non-italic part)

*So I here I am, asking, nay, begging for help in installing Java, and other essential programs. Hopefully, some kind person (or people) will have pointed me in the direction of (or left) some *very* basic instructions on installing Java for the very ignorant and long time Windows XP user by the morning when I come back to my computer screen with a fresh mind (so I may be more able to learn Ubuntish)*.[I] Please assume I know nothing about PCs, Linux, Ubuntu. I do however, know basic Terminal commands, such as cp, mv, rv, cd.

To those who offer a portion of their knowledge, I thank them with the most heartfelt of thanks.

[/I]Basically, to cut a long story short, I need to install Java on my Ubuntu v 10.04, and know next to nothing. I tried and failed to install it.

Please help me.

Thanks, Tom.

Do this: open a teminal window   (APPLICATIONS > ACCESSORIES > TERMINAL).  At the command line, type this: sudo apt-get install ubuntu-restricted-extras   Press the ENTER key and watch stuff scroll by. :-)
This should get you JAVA installed.  To verify, go to SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER and in the search box type  jre  for your search.  It should come up with a green block in front of jre****  That means it is installed.  If the box is not green, click on it to install and follow the directions.

---

### Post by tomnewton on 2010-06-06
Arggh!

Tried what you suggested Autodave, but it said 'E: the package sun-java6-jre needs to be reinstalled, but I can't find the archive for it.'

What do I do?

Could you tell me how to uninstall everything to do with Java so I can start again from the beginning?

Thanks

---

### Post by diablo75 on 2010-06-06
> **tomnewton said:**
> Well, here I am, back in the morning, but not in my usual spot. I wake and find, to my shock, my spot at my desk has been usurped by my sister playing on my desktop PC.

First, thanks to you three who left replies.



Secondly, I tried the first option first (this one ^ ), and I followed the instructions it gave me in the Terminal (I wasn't sure what it meant when it said 'we'll add', I assumed the Terminal). I ran up against a set of license agreements that I didn't know how to click OK to.  It just OK in text...

How do I agree?

Thanks, Tom.
[I]
On a side note, is there a shortcut for switching between the workspaces that are shown in the bottom right? If so, what is it? Thanks.[/I]

Hit the TAB key on your keyboard to switch between buttons inside one of those text-based GUI's in a terminal, then press spacebar or Enter.

---

### Post by tomnewton on 2010-06-06
> **diablo75 said:**
> Hit the TAB key on your keyboard to switch between buttons inside one of those text-based GUI's in a terminal, then press spacebar or Enter.

Thanks, I worked out how to start over (on my own, v. proud of that. Applause please =D>. Thank you, thank you).

I re-ran the installation, and it's installing happily now I agreed to the license agreement.
[I]
EDIT: Java works fine now, thanks all of you chaps![/I]

---

