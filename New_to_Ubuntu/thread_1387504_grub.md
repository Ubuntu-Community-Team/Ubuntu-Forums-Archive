---
title: "grub"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by kmsalex on 2010-01-21
I was just curious when I boot up my computer and get grub i am presented with 7 possible options, 
ubuntu, linux 2.63.31-17-generic
ubuntu, linux 2.63.31-17-generic (recovery mode)
ubuntu, linux 2.63.31-14-generic
ubuntu, linux 2.63.31-14-generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+)serial console 115200
windows 7
I have 2 questions.

1. what is the difference betewn
ubuntu, linux 2.63-17-generic
 &
ubuntu, linux 2.63-14-generic

2. how do you move the options up or down the list?
like if i want to make windows the default.

---

### Post by tom.swartz07 on 2010-01-21
> **kmsalex said:**
> I was just curious when I boot up my computer and get grub i am presented with 7 possible options, Linux kernel ####.17 Linux kernel ####.14 each of which have a recovery mod option pulse 2 ram test options. and lastly the windows 7 option. now I have 2 questions.

1. what is the difference betewn the 2 different linux kernal options ####.17 and ####.14

2. how do you move the options up or down the list?

Theres basically no difference between the two kernels in the list. Its *usually* recommended that you keep at least one previous kernel in case something goes wrong, but youre probably safe removing it.

In synaptic package manager, just search for 'linux image' and remove the one ending in .14


Im not too sure about moving boot options up and down the list- I personally havent tried anything like that recently. Perhaps someone else could provide info on that. Ill look into it and get back to you

---

### Post by cenzorrll on 2010-01-21
this is my new favorite thread on these forums, tells you all about grub2 
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

(I'm assuming you installed 9.10 not any of the older versions of ubuntu, if you did install one of the others, then you can just edit your /boot/grub/menu.lst **DO NOT do so until after you've read about what this file does and how to edit it**)

---

### Post by kapmsd on 2010-01-22
@Kmsalex:

Why do u want to move the boot options up/down the list?

If u want to change the boot option,u can very well edit the /boot/grub/menu.lst file.

---

### Post by kmsalex on 2010-01-22
> **kapmsd said:**
> @Kmsalex:

Why do u want to move the boot options up/down the list?

If u want to change the boot option,u can very well edit the /boot/grub/menu.lst file.
i'm on the line about making windows the defualt.

---

### Post by ranch hand on 2010-01-22
I would really like to know what version of Ubuntu you are using.  9.04 uses the 2.6.28 kernel, 9.10 the 2.6.31 kernel, 10.04-testing the 2.6.32 kernel.

You use the 2.63?  Far out.

---

### Post by tjsummers51l on 2010-01-23
To change the default setting, just install startup-manager from Ubuntu software center. You can make those changes there pretty easily.

---

### Post by 416inversed on 2010-01-23
> **kmsalex said:**
> i'm on the line about making windows the defualt.
You can change the default setting from Start-up Manager.

To install from terminal
```
sudo apt-get install startupmanager
``` Then it'll be under System, Administration.

EDIT: or you install like tjsummers51l mentioned....

---

### Post by ranch hand on 2010-01-23
Or, if you are not addicted to the MS "get another app to do it for you" habit - you could just go to /etc/default/grub and change the "default=0" to what ever number your chosen OS is on your menu (counting starts with 0 so if it is second in the menu you would change 0 to 1).  Save. Run "sudo update-grub".

---

### Post by tjsummers51l on 2010-01-23
It's amazing. Ubuntu is "designed" around making things easier. Isn't that what they are telling people in order to get them to try it out. I for one am happy that I don't have to use th shell as much anymore.

---

### Post by kmsalex on 2010-01-23
> **ranch hand said:**
> I would really like to know what version of Ubuntu you are using.  9.04 uses the 2.6.28 kernel, 9.10 the 2.6.31 kernel, 10.04-testing the 2.6.32 kernel.

You use the 2.63?  Far out.

no it was a typing error on my part, i edited my original post to reflect the correct kernel.

side question, the memory tests, what's the difference between them?

---

### Post by ranch hand on 2010-01-23
It is easier.  Here we have someone who wants to change the way the system works.  There is nothing wrong with that.

There is something wrong with mindlessly installing some thing to do this for you.  You really should know how before deciding to add another layer between your self and control of your own box.

I am on 9.04 right now.  This is my night time production OS.  It has SUM on it.  I don't use it because the grub on the MBR is from PhatDebian with grub1.96 installed.  Tomorrow morning I will be back on 10.04-testing.

I do not keep up with SUM development because I do not use it but I do know that the developer had to wait for grub2 to be released before really working on making it work with grub2 and there were some conflicts.  I am sure that you can change default wit hit.

If there are still conflicts that cause other problems with grub, are you prepared to fix them?

---

### Post by ranch hand on 2010-01-23
> **kmsalex said:**
> no it was a typing error on my part, i edited my original post to reflect the correct kernel.

side question, the memory tests, what's the difference between them?
Not a thing, there is one for each kernel entry.  That is why you have 2 of them.

If you want to know more about grub check the link in my sig.  The second link in that post is the best in depth grub info you are going to get.  Mine is just an over view.

We all learned a lot in a hurry during 9.10-testing when grub2, with no documentation, hit use at the alpha2 mark.

---

### Post by kmsalex on 2010-01-23
thanks for the explanations and links every one.

---

