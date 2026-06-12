---
title: "Could not apply the stored configuration for the monitor"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by Nikola Georgiev on 2011-06-10
I was just changing users when this happened.
When I try to log in I get a "Could not apply the stored configuration for the monitor. Could not find a suitable configuration of screens." message in the right top part of my screen. I log in and that's it. Black screen. I can't access the Run, nor the Terminal.
Now I'm using the Live CD (the Ubuntu installation CD -> "Try Ubuntu").


I tried finding a solution on the net, but with no luck. Please help.

---

### Post by Nikola Georgiev on 2011-06-11
Am I posting in the wrong section? :-k

---

### Post by grahammechanical on 2011-06-11
No. Not really. Perhaps no one knows the answer. When you boot do you get an option to load in low resolution mode? You may have a video adapter that is becoming faulty. It could be overheating.

This happened to me the other year. I could only boot into low resolution mode. Then even the Live CD would not work.

I think that when the OS boots it reads some settings from the monitor that tell it the resolution. It uses the video adapter to do this. In my case the video adapter was not getting the information that the OS needed from the monitor. A new video adapter fixed things by which time I had messed up the OS and had to reinstall.

I would suggest that you back up all your important files while you can and then find what the monitor settings are. Then examine the X server configuration files and edit them to put the correct information in.

Regards.

---

### Post by Nikola Georgiev on 2011-06-12
I don't got an option to load in some type of resolution.
Also, I don't have another HDD to back up my info. :/
Can you give me an option that I wouldn't have to format and I'll be able to reinstall/restore Ubuntu to the default state, so I can use my comp once again?
I'm ****** up  and desperate. And I don't want to go back to windows, so please, give me an option. 
Maybe Ctrl+Alt+F1 and some writing in the console? :?

Thanks in advance.

---

### Post by jtarin on 2011-06-12
Can you login as another user....normally?

---

### Post by Nikola Georgiev on 2011-06-13
> **jtarin said:**
> Can you login as another user....normally?
No.

---

### Post by jtarin on 2011-06-13
Quote:
> Originally Posted by jtarin View Post
Can you login as another user....normally?
No. 

> **Nikola Georgiev said:**
> I was just changing users when this happened.
You cannot login as another user...you say, but why were you changing users and how did you attempt this?

---

### Post by jtarin on 2011-06-13
If you can get to the login screen you can switch to another virtual terminal and login as root and add a new user.

---

### Post by Ni-el on 2011-06-13
I have this problem when I upgraded to natty 11.04. The right side of the screen is too small by about 2cm, and it starts by saying that it could not apply the stored configuration. The same issue occured when trying to install Fedora15 and the latest openSuse. I have posted every where and there are no answers. The best thing would be to reinstall Maverick 10.10 until someone catches this problem. I, myself, went to the latest Debian because I don't want to give up the ship.

---

### Post by jtarin on 2011-06-13
List as much information about your monitor identity as you can.
Also post the results of the command "lspci"

---

### Post by Nikola Georgiev on 2011-06-15
> **jtarin said:**
> List as much information about your monitor identity as you can.
Also post the results of the command "lspci"
can't access that command "lspci" from the Terminal, I'm still using that Live CD...
[**This**](http://ubuntuforums.org/showthread.php?t=1706707) might be helpful finding an answer, and It may be connected. But It was months ago.

---

### Post by jtarin on 2011-06-15
Try to access your installed system to make those same changes. Use the Live CD and the [CHROOT]("https://help.ubuntu.com/community/Grub2#ChRoot") method to gain access to your installation as root. Skip steps 8,9, and 10.

---

### Post by Nikola Georgiev on 2011-06-16
> **jtarin said:**
> Try to access your installed system to make those same changes. Use the Live CD and the [CHROOT]("https://help.ubuntu.com/community/Grub2#ChRoot") method to gain access to your installation as root. Skip steps 8,9, and 10.
Ok. And then what?
That only restarted my comp.

Can't I somehow just restore my whole configuration to it's basic default settings?
Or just format the partition where I installed Ubuntu, and reinstall it from the beginning?

---

### Post by jtarin on 2011-06-16
> **Nikola Georgiev said:**
> Ok. And then what?
That only restarted my comp.

Can't I somehow just restore my whole configuration to it's basic default settings?
Or just format the partition where I installed Ubuntu, and reinstall it from the beginning?You should have accessed Ubuntu install and reconfigured your monitor as you did in your other post at step #7.

---

### Post by wildmanne39 on 2011-06-16
> **Nikola Georgiev said:**
> Ok. And then what?
That only restarted my comp.

Can't I somehow just restore my whole configuration to it's basic default settings?
Or just format the partition where I installed Ubuntu, and reinstall it from the beginning?
Hi, you can always just reformat and reinstall like you said, that is up to you, you can use the livecd to do it.

---

### Post by Nikola Georgiev on 2011-06-16
> **jtarin said:**
> You should have accessed Ubuntu install and reconfigured your monitor as you did in your other post at step #7.
Well, ether I can't understand you fully, or I just can't do it right.

> **wildmanne39 said:**
> Hi, you can always just reformat and  reinstall like you said, that is up to you, you can use the livecd to do  it.
If everything else can't do it, I'll do that.



Right now I **can** access my system, but without the graphical interface. Can that be useful?
And I don't know the Terminal's main commands like copy-paste, going to a directory or anything useful. I don't have the necessary knowledge to use the console on my own.

---

### Post by jtarin on 2011-06-16
> **Nikola Georgiev said:**
> Well, ether I can't understand you fully, or I just can't do it right.


If everything else can't do it, I'll do that.



Right now I **can** access my system, but without the graphical interface. Can that be useful?
And I don't know the Terminal's main commands like copy-paste, going to a directory or anything useful. I don't have the necessary knowledge to use the console on my own.
You gave a link to another post where you solved this problem using the terminal....why is this different now? Just reformat and reinstall....that's what most do anyway. Next time save your data off disk.

---

### Post by Nikola Georgiev on 2011-06-17
Well, at last, I just formated the partition with Ubuntu on it, and reinstalled. Some info lost, but I'll be ok.
Thanks to all of you for the help.
Cheers.

---

