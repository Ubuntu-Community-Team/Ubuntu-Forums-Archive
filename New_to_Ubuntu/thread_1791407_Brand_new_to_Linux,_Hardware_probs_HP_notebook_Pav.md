---
title: "Brand new to Linux, Hardware probs HP notebook Pavilion DV 7"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by doppleganger09 on 2011-06-26
Hello, You can call me Jay- I have an HP notebook Pavilion Dv7, I was in the studio and my laptop over heated, my hard drive crashed and the only way I knew to start using my laptop again was to install a new operating system, so I lost everything, I lost windows 7 too. I don't know anything about Ubuntu, how ever i've tinkered with it in the past. 
Here's my problem, 
I have A dual Graphics card setup, ATI graphics cards, In windows I was able to switch from power-saving GPU to high powered GPU, I installed the ATI driver Linux provided me already, but when I open catalyst control center, I encounter an error, this is what it says
"   p, li { white-space: pre-wrap; }  No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig. "


Please help!


Also- I have additional problems, I want to disable my track-pad, because i'm using a mouse and my hands keep bumping into buttons, this is the 6th time i've typed this, and had to restart. (Yes i'm counting)- With windows I can just touch my pad on the top left corner 3 times and it goes red and disables the pad. i can't do that with Ubuntu.


another problem- 

I'm a musician, music is my life, and with windows- I used a POD farm program with my Line 6 UX1 pod, it worked perfectly, I remember when I had ubuntu before the crash, I attempted to install my Pod farm Via Wine, the Interface worked... Kind of., but I got no sound, How can I effectively use my Line 6 Pod Ux1 effectively with Ubuntu. 



I really enjoy using Ubuntu (Linux) As I dislike the microsoft corp. But If i can't figure these problems out, i'm afraid I will have to go out and waste money on another copy of windows 7, because Foolishly, I had not made a back-up disk when i got my laptop. Live and learn, right?
Any help would be appreciated, I never have used a forum before- I don't know the rules, So in advance, I am sorry If i am in the wrong thread. You can contact me at [email]Jamiej93@yahoo.com[/email] Or Text me at 218-309-7730 

I need this fixed ASAP For the studio, 

Cheers, and keep it metal!

---

### Post by jtarin on 2011-06-26
I, more than you think understand your situation, but you should post each problem seperately to get the attention it deserves.
As to your track pad.....I don't know your version but [this]("http://www.andrewferrier.com/blog/2010/06/04/disabling-synaptics-touchpad-with-ubuntu-10-04/") might work.

---

### Post by doppleganger09 on 2011-06-26
Thanks for responding to my thread, Can you guide me through this process please? I'm still new to the terminal, I attempted several times, but I just can't figure it out.

---

### Post by jtarin on 2011-06-26
When you see commands printed on a web page you can just copy and paste them in the terminal.....makes it very easy and accurate. Let's do this one, which is the first.```
sudo aptitude install xserver-xorg-input-synaptics gpointing-device-settings

``` Just copy and paste hit enter then it will ask you for your password.....type it.....then hit enter. It will download and install the software. It might ask you if you want to continue....say yes if you do. Then follow the remaining instructions. Post any errors.

---

### Post by doppleganger09 on 2011-06-26
I did that, and this is what i get,

Sudo: Aptitude: command not found

Am I missing anything as far as patches goes?

---

### Post by nzjethro on 2011-06-26
Try

```
sudo apt-get install xserver-xorg-input-synaptics gpointing-device-settings
```

Aptitude and apt-get are both package managers (i.e. they get programmes for you). Apt-get comes preinstalled, while Aptitude does not.

---

### Post by doppleganger09 on 2011-06-26
According to the terminal, i already have it? How can I locate this? This is the message I get

> Reading package lists... done
Building dependency tree
Reading state information... Done
gpointing-device-settings is already the newest version.
xserver-org-input-synaptics is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by doppleganger09 on 2011-06-26
Never mind I figured it out. Now I need to get my ATI catalyst working and figure out how to get my pod to work. Any suggestions? Which thread do I need to look at?

---

### Post by jtarin on 2011-06-26
In the terminal```
gpointing-device-settings
```

---

### Post by jtarin on 2011-06-26
> **doppleganger09 said:**
> Never mind I figured it out. Now I need to get my ATI catalyst working and figure out how to get my pod to work. Any suggestions? Which thread do I need to look at?As I suggested....start a separate thread for each issue. Don't post them all at once. Post one,then when it is solved post another.Board etiquette and also helps you stay ontrack with one problem at a time.

---

