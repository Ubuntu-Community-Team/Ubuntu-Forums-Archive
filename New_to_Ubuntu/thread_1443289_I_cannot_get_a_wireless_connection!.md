---
title: "I cannot get a wireless connection!"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by amr1980 on 2010-03-30
Hi,

I just installed Ubuntu 9.10 from CD.  

I have several issues that are frustrating me to no end!

1.  I cannot get my wireless connection to work (I share my neighbors' connection so I cannot use a wired connection).  It doesn't seem to detect anything at all.  I have a LinkSys WUSB00N wireless adapter. 

I searched around and found a link for some drivers.  However, the instructions ([http://www.linuxquestions.org/questions/linux-newbie-8/rt2870-wusb600n-v-2-not-detected-ubuntu-9-10-a-790915/](http://www.linuxquestions.org/questions/linux-newbie-8/rt2870-wusb600n-v-2-not-detected-ubuntu-9-10-a-790915/)) tell me to navigate to the new folder in the terminal, which leads me to:

2.  I cannot navigate to a folder that is on my desktop in the terminal.  I've read several tutorials and there is something I'm just not getting because no matter what I seem to type, the terminal tells me that there is no such file or directory.  

I have other issues, but I suppose I'll save them for another thread. 

Any help will be greatly appreciated!

Thank you,
Angelo

---

### Post by Shibblet on 2010-03-30
We need to know what kind of wireless adapter you are using.

---

### Post by amr1980 on 2010-03-30
Is the information I gave not what you need?  I don't have any more information than that, unless I'm missing something...

---

### Post by somethingkindawierd on 2010-03-30
When navigating in the Terminal it's useful to know that typing:
```
cd ~/
```
will change you to your home directory.
Typing ```
cd /
```
will take you to the root of your computer.

And, if you want to 'test' for the existence of a folder you can type the first few characters and hit tab...it will auto-complete the folder if it exists. An example of this would be typing:
```
cd /etc/X
```
and then hitting tab...you should see it auto-complete the X11 folder name.

---

### Post by amr1980 on 2010-03-30
First off, thanks for taking this time to help me.

So, if I want to access a file that is on my desktop, what do I do?  The name of the file is WUSB600N.

---

### Post by eyeyoubin on 2010-03-30
go to terminal, which is located at applications->accessories
then type *iwconfig* then post what you get from that.

secondly, say if the file is text file and you want to edit it, type
*gedit /home/yoobin/Desktop/WUSB600N*
make sure you get capital and small letters right.
of course, the command you put in front of file address depends on what you wanna do with it. what do you wanna do it with?

---

### Post by amr1980 on 2010-03-30
it says:
lo              no wireless extensions.

eth0           no wireless extensions.

wmaster0    no wireless extensions.

wlan0          IEEE 802.11abgn   ESSID:" "
                  Mode:Managed    Frequency:2.412 GHz      Access Point:  Not-Associated
                  Tx-Power=0 dBm
                  Retry  long limit:7     RTS  thr: off      Fragment   thr: off
                  Power Management: on
                  Link Quality:0  Signal level:0  Noise level:0
                  Rx invalid nwid:0   Rx invalid crypt:0    Rx invalid frag:0
                  Tx excessive retries:0  Invalid misc:0    Missed beacon:0

---

### Post by flyfishingphil on 2010-03-30
I got confused too until I noticed the little indicator on the top bar, right side, and right clicked on the bars. It then opened up and showed wired or wireless. Just filled in the wireless info and was on line in a few seconds.

You need the name of the wireless router and the password, if secured. That's all it took on mine.

Hope this helps.

---

### Post by amr1980 on 2010-03-30
Mine shows no bars, and I have filled in forms to the best of my ability with no change to my current state.

---

### Post by amr1980 on 2010-03-30
I appreciate the offers for help but I'm at my wits' end for tonight and have to turn in.  

I have to say that so far Ubuntu seems to be a very confusing platform.  Nothing seems to work (music, internet, video, etc.).  

Hopefully tomorrow will bring new answers.

---

### Post by flyfishingphil on 2010-03-30
My error! I looked up and saw the bars and wrote that. It's a little icon between the speaker and the envelope.

---

### Post by somethingkindawierd on 2010-03-31
If you want to access a file on the desktop via the terminal it will be at
```
~/Desktop/WUSB600N
```

---

### Post by amr1980 on 2010-03-31
Well it's day 2 and nothing has improved for me. Ubuntu is pretty much unusable. Almost all instructions I read don't seem to work on my system.  They will refer to folders that don't exist and to commands that aren't allowed.  Surely this OS isn't this convoluted!

So, I'm trying to look for any ideas as to how to connect to a wireless network?  A I said before, the system doesn't even seem to detect my adapter.

Any ideas?

---

