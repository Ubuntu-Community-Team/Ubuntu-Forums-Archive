---
title: "Grub 1.99 problem"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by haluska538 on 2011-07-19
Hello, I have grub 1.99 as it says when I switch on the computer and i wanted to set my windows os as default. However, when I ran menu.lst as it was said in many forums, i coudlnt edit anything, because there was nothing written in there. I have 64-bit computer, but 32bit ubuntu. Could that be a problem?

Thanks forahead :)

---

### Post by Matt__ on 2011-07-19
Install grub customiser.
use these commands one at a time in a terminal:
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update 
sudo apt-get install grub-customizer
```you will get a gui in the applications/system tools menu to manage grub entries.


//edit:[customiser launchpad page](https://launchpad.net/grub-customizer)

---

### Post by Quackers on 2011-07-19
Grub 1.99 is grub2, which does not use the menu.lst any more.
What method did you use to change the default OS to Windows?
The old and trusted way is to edit the line
```
GRUB_DEFAULT=0
``` in the file /etc/default/grub. The "0" refers to the first entry in the grub menu, which is normally the latest installed kernel for your Ubuntu installation.
If Windows is the second entry in the grub menu you would change the "0" in that line to a "1", if Windows is the 4th entry in the grub menu you would change the "0" to a "3", etc, etc. You then save the file, then quit the file.
Then you need to run ```
sudo update-grub
```

---

### Post by haluska538 on 2011-07-20
Well, I got to the grub file, and when I tried to edit it anyhow, I could not, because it is read-only file. I wanted to chnage these permissions, but I couldnt because it says that I am not an owner to change it. Its funny because, there is only one account on my ubuntu, and its freshly installed. Any tips?

---

### Post by linuxman94 on 2011-07-20
To get permission to open a file that is owned by root, you should use sudo.  So enter this command into the terminal and a password dialog will come up.  Once you enter your password, the file will appear in gedit.

```
gksudo gedit /etc/default/grub
```

---

### Post by amjjawad on 2011-07-20
> **haluska538 said:**
> Hello, I have grub 1.99 as it says when I switch on the computer and i wanted to set my windows os as default. However, when I ran menu.lst as it was said in many forums, i coudlnt edit anything, because there was nothing written in there. I have 64-bit computer, but 32bit ubuntu. Could that be a problem?

Thanks forahead :)

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
This is the easiest way!


[**GRUB2 is NOT using menu.lst anymore**]("https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202")!

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by haluska538 on 2011-07-20
Thank you very much, everyone :)

---

### Post by amjjawad on 2011-07-20
> **haluska538 said:**
> Thank you very much, everyone :)

You most welcome ;)

Please let us know if you need anything else!

Good luck may the Linux be with you ;)

---

### Post by Quackers on 2011-07-20
Happy days :-)

---

### Post by haluska538 on 2011-07-20
Just let you know: The program startup manager probably doesnt work properly, because thought I set Windows as default it made ubuntu as default - first highlighted option in grub anyway. So I had to set it through the text document grub as a default... And two additional questions: 
1.How was I supposed to know that I have grub v.2 when it says 1.99? 
2.What does (loader) means? It is written after Windows 7 in grub booting menu.
:confused:

---

### Post by haluska538 on 2011-07-20
This is strange. Althought the default is no.6 - which is windows, the computer still after restarting highlights the first option-ubuntu...:confused:

---

### Post by amjjawad on 2011-07-20
> **haluska538 said:**
> Just let you know: The program startup manager probably doesnt work properly, because thought I set Windows as default it made ubuntu as default - first highlighted option in grub anyway. So I had to set it through the text document grub as a default... And 


Never had any problem using Startup Manager.
I had it installed in Mint 11 on a Toshiba Laptop and Dual-Booting with Win7. It works perfectly.


> 1.How was I supposed to know that I have grub v.2 when it says 1.99? 

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)


> 2.What does (loader) means? It is written after Windows 7 in grub booting menu.

[http://en.wikipedia.org/wiki/Loader_%28computing%29](http://en.wikipedia.org/wiki/Loader_%28computing%29)

and in this case, it's Windows 7 Boot-Loader

---

### Post by Quackers on 2011-07-20
After editing /etc/default/grub did you click on File > save, then File > quit then run sudo update-grub?

Also it may be that startup manager has not been updated to work with the latest grub versions. I think that may have happened before.

---

### Post by amjjawad on 2011-07-20
> **Quackers said:**
> Also it may be that startup manager has not been updated to work with the latest grub versions. I think that may have happened before.

If I'm not wrong, the latest Kernel in Linux Mint 11 (which is installed on one of the machines at my home) is 2.6.38. Not very sure though!

---

### Post by wildmanne39 on 2011-07-20
Hi, apparently this is not working yet for grub2, I am sorry I thought it was.

---

### Post by Quackers on 2011-07-20
wildemanne39 does that work with the latest versions of grub 1.99? At one time it didn't :-(

---

### Post by wildmanne39 on 2011-07-20
> **Quackers said:**
> wildemanne39 does that work with the latest versions of grub 1.99? At one time it didn't :-(Hi, I have used grub customizer for adding images to the boot menu but I have not tried to change the boot order because I like booting ubunbtu first, but I have done more research and it does look like that is being worked on and is not working yet. 

So you are correct, thank you for letting us know and I am going to change my post.

---

### Post by Quackers on 2011-07-21
Thanks for the clarification. To be honest grub seems to be changing so fast it must be hard for them to keep up.

---

### Post by amjjawad on 2011-07-21
> **haluska538 said:**
> This is strange. Althought the default is no.6 - which is windows, the computer still after restarting highlights the first option-ubuntu...:confused:

Startup Manager - As attached, after you make your selection, click Close and reboot.

It should work.


Again, I'm using Startup Manager which is installed by default in Linux Mint 11.

---

### Post by haluska538 on 2011-07-21
Well I tried everything written above... Look at the pictures - thats how I set it and it still does not work. Would grub customizer help me?

---

### Post by amjjawad on 2011-07-21
> **haluska538 said:**
> Well I tried everything written above... Look at the pictures - thats how I set it and it still does not work. Would grub customizer help me?

Does your machine boot into Windows anyway?

By the way, I suggest to increase the timeout to 10 sec. Just a note, has nothing to do with your problem.

As for GC, I found this: [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by Quackers on 2011-07-21
When /etc/default/grub has been edited have you saved the file then run sudo update-grub?
Please post the output of ```
sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2
```

---

### Post by haluska538 on 2012-03-15
Hello guys, sorry for posting so late, I just wanted to tell you, that I already solved this problem with my pal, neither one of those softwares (SatrtUp manager or Grub Customizer) worked for me so we simply ran Terminal and typed in "sudo gedit /boot/grub/grub.cfg" and adjusted it manually including the resolution. Thanks a lot for your help anyway! :) :guitar:

---

