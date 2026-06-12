---
title: "is this a partition problem? pls help."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by dogafin on 2009-01-18
it seems i have two instances of ubuntu on my system. i have updated from hardy to ibex (8.04 to 8.10) now instead of just having one os's i now have two of the same but different kernel??

i wish to remove one, doesnt matter which one, i just want to keep one and not both since i do not have much memory on my hard drive. (80 gb)

i can solve my problem the looong way. reinstalling windows xp to format the hard drive and then reinstall ubuntu 8.10 from cd. i am trying to avoid this. 
please help
here is a screenshot:

[IMG]http://i40.tinypic.com/33agr2h.jpg[/IMG]

---

### Post by taurus on 2009-01-18
You have two kernels (not two OSes), one from hardy and one from intrepid.  If you want to remove the older kernel, 2.6.24.23, go into synaptic and remove it from there.

---

### Post by Crafty Kisses on 2009-01-18
Well it would depend on what kernel you wanted to keep, you would have to edit GRUB to remove one of those from the list:
```
/boot/grub/menu.lst
```
You could also remove one of them from Synaptic, it's really your choice.

---

### Post by insilicium on 2009-01-18
I have the same problem.  It seems that this happens every time the kernel gets updated - the grub loader hangs on to the old one just in case there are any problems with the new kernel.  This is getting obnoxious though, as each new update causes another two items to scroll past to get to Windows at the bottom!

It seems that there should be a way to remove the old kernel in Synaptic, but I haven't found anything yet.  Suggestions?

---

### Post by dogafin on 2009-01-18
oh! that is good to know! i was thinking there are two copies of them. ill see what i can do around synaptics.gosh, had i known this before!! 

thank you so much!:KS
-----------------------------------
wow more replies! cant get em worked out through synaptics? i will try that and if i too run into that problem id have to pull up the grub menu list as codename has suggested.
-----------------------------------
dogafin@dogafin-desktop:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
dogafin@dogafin-desktop:~$ 

this is what i got with the menu list. now i am stuck with one option, going thru synaptics. but since im such a noob, idk what to search for, i can type kernel and see something familiar but i am not sure really what to do..

codename, we need u back!

---

### Post by arpanaut on 2009-01-18
Removing from menu.list will not free any space on your HD 

but removing the packages through synaptics will!

common practice is to leave at least one instance of the old kernel installed...
"Just in case"

---

### Post by thomas228 on 2009-01-18
> **insilicium said:**
> I have the same problem.  It seems that this happens every time the kernel gets updated - the grub loader hangs on to the old one just in case there are any problems with the new kernel.  This is getting obnoxious though, as each new update causes another two items to scroll past to get to Windows at the bottom!

It seems that there should be a way to remove the old kernel in Synaptic, but I haven't found anything yet.  Suggestions?

Hi

Try installing Startup-Manager.  Use synaptic package manager under administration. Search function for Startup-Manager.allows option of how many version,color and a few others

If you use sudo gedit /boot/grub/menu.lst copy your windows at the bottom to ahead of ### BEGIN AUTOMATIC KERNAL LIST This is a terminal command. Putting windows ahead of  ...LIST will make it your first choice on the grub menu.

Good Luck
Tom

---

### Post by Marshal0505 on 2009-01-18
Correct me if i'm wrong but would an installed kernel take up something like 100mb room?I understand the need to keep things tidy and clean.But in terms of space you would gain very little.I think it's good practice to atleast have 2 kernels installed for possible future troubleshooting purposes.

So in short:Remove old kernels? Sure... but try to have atleast two installed.(imo)

---

### Post by dogafin on 2009-01-18
okay ive payed the good ole google search a visit and came across this thread:

[http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

i was able to remove a line with the old kernel from the synaptics by searching for **linux-image**. ive yet to start up and make sure it isnt there anymore. but i saw one line with the old kernel that is installed (with a green box) and marked it for uninstallation.

also, just to make sure what u are using i also did what the thread says, to type in **uname -a** in the terminal.

will come back and let u guys know
------------------
after restart:
[IMG]http://i44.tinypic.com/2mr6v5y.jpg[/IMG]
this worked out for me guys :)
thank you for all the help.

---

### Post by DylanW on 2009-01-18
> **Marshal0505 said:**
> Correct me if i'm wrong but would an installed kernel take up something like 100mb room?I understand the need to keep things tidy and clean.But in terms of space you would gain very little.I think it's good practice to atleast have 2 kernels installed for possible future troubleshoting purposes.

So in short:Remove old kernels? Sure... but try to have atleast two installed.(imo)

I was going to say what he did

but also, if you want to rearrange the order of the selections

```
sudo gedit /boot/grub/menu.lst
```

the different selections will be grouped like below with a blank line between them, just cut and paste them in the order you want

```
title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=aea67a09-6e4f-4b05-a957-b55c885b8157 ro quiet splash
savedefault
```

---

### Post by kansasnoob on 2009-01-18
Just install startupmanager either from synaptic or:

```
sudo apt-get install startupmanager
```

Under the "advanced" tab you'll see an option to limit the number of kernels kept. You could also untick the memtest option (how often do you use that?)

Other stuff:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

