---
title: "Installation problem"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by bj218 on 2010-06-23
I just installed Mint8. I previously had Mint7 installed. After installing
Mint8 my start up screen still shows Mint7 & when I clk on it I get nothing.
When I installed 8 I unchecked Boot loader as I wanted to keep the same boot sequence ie Ubuntu WinXP Mint. What can I do to get Mint8 to work?

---

### Post by QIII on 2010-06-23
Are you still running Jaunty as your information says?

---

### Post by bj218 on 2010-06-23
> **QIII said:**
> Are you still running Jaunty as your information says?

I installed Mint8 on the same partition that Mint7 was on. I think Mint8 should have reformatted that partition before doing the installation of 
Mint8!!

---

### Post by AgentZ86 on 2010-06-23
So, your boot screen still works right ? 

Such as Ubuntu and Windows but your just having problems with Mint8 ?

But I do believe you have to format the Mint8 partition.
And also I think Mint8 includes Grub2 so I'm not sure it can boot from the Grub1 on Jaunty Ubuntu or not ?

Here is a link regarding Grub
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But I'm not sure exactly what parts of this will be relevant or if this is the case regarding Grub2 but it sounds related.

I hope this helps.

---

### Post by QIII on 2010-06-23
The reason I ask about Ubuntu is because I am assuming GRUB or GRUB2 is installed there.

Jaunty uses GRUB, Lucid and later use GRUB2.

If you are booting via GRUB or GRUB2 on your Ubuntu partition, we need to take a look at your GRUB/GRUB2 configuration and see if it needs to be updated.

If you are running Lucid, you should just be able to use the terminal and issue

```
sudo update-grub2
```

to get it sorted out.

---

### Post by bj218 on 2010-06-23
> **QIII said:**
> The reason I ask about Ubuntu is because I am assuming GRUB or GRUB2 is installed there.

Jaunty uses GRUB, Lucid and later use GRUB2.

If you are booting via GRUB or GRUB2 on your Ubuntu partition, we need to take a look at your GRUB/GRUB2 configuration and see if it needs to be updated.

If you are running Lucid, you should just be able to use the terminal and issue

```
sudo update-grub2
```

to get it sorted out.

I think Ubuntu & Mint are grub2 maybe the 2 attachments will help.

---

### Post by bj218 on 2010-06-23
> **AgentZ86 said:**
> So, your boot screen still works right ? 

Such as Ubuntu and Windows but your just having problems with Mint8 ?

But I do believe you have to format the Mint8 partition.
And also I think Mint8 includes Grub2 so I'm not sure it can boot from the Grub1 on Jaunty Ubuntu or not ?

Here is a link regarding Grub
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But I'm not sure exactly what parts of this will be relevant or if this is the case regarding Grub2 but it sounds related.

I hope this helps.

1. N0t for Mint
2.Yes
3.Ubuntu is grub2 but I don't know for sure if Mint8 is grub2.

---

### Post by AgentZ86 on 2010-06-23
> **bj218 said:**
> 1. N0t for Mint
2.Yes
3.Ubuntu is grub2 but I don't know for sure if Mint8 is grub2.

Ok Mint8 uses grub2

But from the link it also says this:
If you are running Ubuntu Jaunty or Intrepid, you are running Grub Legacy.

So that would not be Grub2.

Anyhow:
#Grub Legacy uses boot/grub/menu.lst.
#Grub 2 uses uses boot/grub/grub.cfg. 

I think Mint7 uses Grub Legacy

Having said that let me ask about your boot sequence ? 

As you mentioned:
> ie Ubuntu WinXP Mint. What can I do to get Mint8 to work?


So I'm assuming that Ubuntu is your boot OS using Grub2 ? and not Jaunty or Intrepid which is Grub Legacy ?

If that is the case then You may not need to format or re-install Mint8 but simply need to re-configure Grub2 as described below.

#Grub 2 uses uses boot/grub/grub.cfg. 

Or you can use this command in the terminal as mentioned in the link I posted:
> sudo update-grub2

This should find your OS's again if Mint8 is not there and still showing Mint7 it's likely Grub2 is not finding it in the (boot/grub/grub.cfg.) file

So the command should fix this.

If your default boot loader is not Ubuntu with Grub2 then this is another subject.

I hope this helps.

---

### Post by bj218 on 2010-06-24
I ran "sudo update-grub2 & now Mint7 is no longer on the startup list in fact there is no Mint on the startup list. Do I need to install Mint8 again?
Another question is their a command for grub2 that will allow me to edit it?
In my old grub I used "sudo gedit /boot/grub/menu.lst.

---

### Post by AgentZ86 on 2010-06-27
> **bj218 said:**
> I ran "sudo update-grub2 & now Mint7 is no longer on the startup list in fact there is no Mint on the startup list. Do I need to install Mint8 again?
Another question is their a command for grub2 that will allow me to edit it?
In my old grub I used "sudo gedit /boot/grub/menu.lst.

Thats sounds right either NO mint should be on the startup list or it should have updated it ?

If you have grub/menu.1st then you have legacy grub and not grub2 which would explain why it did not update anything other then to to take it off the list, but not sure why it would do anything if it's not grub2 ? 

The grub you need to edit for grub2 is:
#Grub 2 uses uses boot/grub/grub.cfg.

But if you have an old grub/menu.1st then I'm assuming this is located in your /boot/grub/menu.1st of your Ubunutu partition ? Right ? and this would be grub legacy ?
But if it's an old menu.1st because you upgraded to grub2 then you should have grub.cfg which is the one that should have updated, so I'm not sure why it didn't ? 

When you say old /menu.1st ? this confuses me ?

Are you sure you have grub2 on ubuntu ?

Try this for grub legacy and see what happens ?
> 
sudo update-grub

> [http://www.dedoimedo.com/computers/grub-2.html#mozTocId293325](http://www.dedoimedo.com/computers/grub-2.html#mozTocId293325)

also take a look here this might be helpful to know too

> [http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

A little techno jargon but worth the research.

I had a heck of a time getting my system back up after re-installing windows which basically wiped out grub completely

I did this reading which really gave me a headache, but got my system back up and didn't lose any Ubuntu stuff it was such a relief LOL

Anyhow sorry for the delay and hope this helps.

Also this info here on the Ubuntu site was more then I wanted to know but will help me in the future with whatever I do on dual booting now.

Duplicate link from before but it's helpful, you may need about 1-2 hours with frequent breaks to sort thru this info and understand it all but once you do you will not run into this problem again that you can't solve.


[QUOTEhttps://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows][/QUOTE]

Let me know if you need more help.
Happy Hacking

P.S
> GRUB 2 is version 1.98 or later. GRUB legacy (version 0.97) will be referred to as GRUB. To determine your version, use grub-install -v

And you can upgrade to Grub2 here also:
You could try running the sudo update-grub2 again after you update, if the update-grub does not work.
> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Anyhow Happy Hacking

---

### Post by bj218 on 2010-06-27
I am a bit confused it looks like I don't have either grub!!

I just did attachment 4 & I now have Mint!!! There is only one Mint entry
however but that is all I really need? Thanks I really appreciate all your help.

---

