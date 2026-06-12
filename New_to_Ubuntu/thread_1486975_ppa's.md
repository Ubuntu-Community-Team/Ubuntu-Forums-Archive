---
title: "ppa's?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by 2roombas on 2010-05-18
I use 9.04 (Jaunty) and the kmyoney in the repos is .9 (something like that). and I want to put 1.0 on this old desktop. I have 1.0 on my laptop running lucid, but can't gt lucid on this old dell dimension 2350 (those intel graphic card issues).

So I looked up how to get kmymoney 1.0 and was directed to this page [HERE]("https://launchpad.net/~claydoh/+archive/ppa"). Can someone please explain to me what I am to do next? I've never installed anything this way before. Thanks!

---

### Post by Chesamo on 2010-05-18
[https://help.ubuntu.com/community/Repositories/CommandLine#Adding Launchpad PPA Repositories](http://bit.ly/d1svWA)

---

### Post by 2roombas on 2010-05-18
Thank you, but I'm not really sure what all that means (I'm still in the newbie/learning stage with Linux.... loving it!). Plus it says it is for 9.10, I'm using 9.04.

I guess my question is.... looking at this page [HERE]("https://launchpad.net/~claydoh/+archive/ppa"), what do I do (newbie steps, please) to install kmymoney 1.0 on this 9.04 desktop computer.  Where is the file I'm to add? And how do I add it??

---

### Post by spydeyrch on 2010-05-18
Here is an excerpt taken directly from the website that you linked in the post above me. Hopefully it helps:

**On older (pre 9.10) Ubuntu systems**

             **Step 1:** Visit the PPA's overview page in  Launchpad.       Look for the heading that reads Adding this PPA to your system and  click       the *Technical details about this PPA* link.     
             **Step 2:** Use the *Display sources.list*  entries       drop-down box to select the version of Ubuntu you're using.     
             **Step 3:** You'll see that the text-box directly  below       reads something like this:     
                      deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) jaunty  main
        deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) jaunty  main           
           Copy those lines.    
           **Step 4:** Open a terminal and type:    
           sudo gedit /etc/apt/sources.list    
           This will open a text editor containing the list of archives that  your      system is currently using. Scroll to the bottom of the file and  paste the      lines you copied in the step above.    
           Save the file and exit the text editor.    
           **Step 5:** Back on the PPA's overview page, look for  the      *Signing key* heading. You'll see something like:    
           1024R/72D340A3 (What is this?)    
           Copy the portion after the slash but not including the help link;  e.g.      just 72D340A3.    
           **Step 6:** Now you need to add that key to your  system so      Ubuntu can verify the packages from the PPA. In your terminal,  enter:    
           sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys      72D340A3    
           Replace 72D340A3 with whatever you copied in the step  5.    
           This will now pull down the PPA's key and add it to your system.    
           **Step 7:** Now, as a one-off, you should tell your  system      to pull down the latest list of software from each archive it knows      about, including the PPA you just added:    
           sudo apt-get update    
           Now you're ready to start installing software from the PPA!    



If you need any steps clarified, just ask. :)

-Spydey :guitar:

---

### Post by jbcfarina on 2010-05-18
Click technical details  in the web, select Jaunty in the box,

Go to software Sources (In spanish it's origin, I don't know which word it's exactly, you should find it in System/Administration/Software Sources,Origin?
Go to the tab about Other Software, click Add button,then,

1. Copy paste the line yo could see in the web
deb [http://ppa.launchpad.net/claydoh/ppa/ubuntu](http://ppa.launchpad.net/claydoh/ppa/ubuntu) jaunty main
2. Click on signing key on the web, and then to the number and save the web
as key.txt for example

Then select tab Authentication in Software Sources, and select import key, select your key.txt

So now you could update && upgrade, good luck, and sorry I don't know the exact words for software source
in an English installation. 

Anyway you should try to install lucid, I also got an Intel and no problem, I thought Jaunty was buggy with intel hardware?:)

---

### Post by jbcfarina on 2010-05-18
Now you know two ways, have fun !! :popcorn:

---

### Post by spydeyrch on 2010-05-18
> **jbcfarina said:**
> ....... sorry I don't know the exact words for _**software source**_
in an English installation. 

Actually, you said it already. :P

(Siempre se me hace un poco chistosito cuando uno no se acuerda de la traduccion y no se da cuenta de que ya la dijo. A mi, me pasa con mucha frecuencia. :))


-Spydey :guitar:

---

### Post by 2roombas on 2010-05-18
Thank you! :)

> **jbcfarina said:**
> Anyway you should try to install lucid, I also got an Intel and no problem, I thought Jaunty was buggy with intel hardware?

I tried lucid, but had to reinstall jaunty.:(   It seemed to behave just fine for a while, then I had [this problem.]("http://ubuntuforums.org/showthread.php?t=1471219")

---

