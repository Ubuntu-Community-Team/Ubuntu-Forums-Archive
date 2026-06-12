---
title: "Activation of network connection failed Ubuntu 20.04"
date: 2021-01-15
forum: Networking &amp; Wireless
---

### Post by asdfsdfgsdfgaefweafersgs on 2021-01-15
I am sorry if something like this has been posted already.  I have severe anxiety and I have to do something constructive, and searching through thousands of posts will only make my already severe anxiety much worse.  

Anyway, I have a Dell Inspiron N1150, and I just installed Ubuntu 20.04 on it.  Even during installation I was not able to connect to the Internet and I thought it was just the wireless card being dumb, since it already didn't work very well when I had Windows on it.  Unfortunately, once installation finished, no matter what I did, and no matter which network I chose, I kept getting the following error:  "Activation of network connection failed"

I have used Ubuntu before, but I still consider myself a total newbie, and all of the steps I've tried already have failed.  I truly don't know what to do.

---

### Post by ajgreeny on 2021-01-15
Moved to Networking & Wireless as a better fit.
See Wireless-Info in my signature below and follow the instructions there to run the script and post the output back here using pastebin if necessary.

---

### Post by asdfsdfgsdfgaefweafersgs on 2021-01-15
I managed to get the script on the computer, but I am having trouble running it.  I must be doing something wrong, but I don't know what.

---

### Post by QIII on 2021-01-15
We can't know what you are doing wrong unless you tell us what you are doing.

Would you please paste the exact command(s) you are entering in the terminal and the results?

---

### Post by asdfsdfgsdfgaefweafersgs on 2021-01-15
So the link I clicked on didn't have any actual instructions, so I had to go to several different tutorials online to cobble together a script file using Notepad in Windows and saving it with the extension .sh.  So I put it on a thumb drive and then connected the thumb drive to the computer with Ubuntu, and tried several times to run the scripts.

You can see the miserable output here:  [https://www.dropbox.com/s/068xnoe13w1uzxg/Photo%20Jan%2015%2C%207%2053%2001%20PM.jpg?dl=0](https://www.dropbox.com/s/068xnoe13w1uzxg/Photo%20Jan%2015%2C%207%2053%2001%20PM.jpg?dl=0)

Basically, I created a bin folder in my Home directory, made it executable, plopped the script file I created in there and then ran the following command:  ./wireless-info.sh

And nothing ever worked.

EDIT:  I connected the laptop to my router via Ethernet and that worked perfectly fine.  I suspect it's the Wifi card or something.  I have an old Wireless G USB device but it didn't work either - I suspect that there is no driver for that.  I might try tethering the laptop to my phone via USB, if possible.

---

### Post by CelticWarrior on 2021-01-16
If you have an alternative internet connection then you can perfectly go the aforementioned link with the script and instructions to run it. It's really that simple.

---

### Post by asdfsdfgsdfgaefweafersgs on 2021-01-16
Unfortunately I&#8217;m not that smart. In fact, I am not smart at all. I need detailed, step by step instructions on how to run that script, because when I clicked that link, all I got was the script code - I went through it line by line and saw no 8nstructuons of any kind.

im sorry I&#8217;m an idiot. I am sorry that I am not smart. I need a lot of hand walking with everything.

---

### Post by coffeecat on 2021-01-16
I must point out to all helping in this thread that there are absolutely **no instructions** in the link ajgreeny provided. It is just the raw bash script, which a newcomer wouldn't know what to do with. 

@ajgreeny, do you have a link to instructions for that script? I don't want to point the OP to the N&W sticky, as they still need a howto to get the raw script into an executable text file.

---

### Post by asdfsdfgsdfgaefweafersgs on 2021-01-16
Okay, I have found the instructions and managed to copy and paste the output into a pastebin, since it is too big to attach.

[https://pastebin.com/gaHUs9TV](https://pastebin.com/gaHUs9TV)

The URL that led me to the instructions is [here]("https://github.com/UbuntuForums/wireless-info").

---

### Post by ajgreeny on 2021-01-17
Yes, sorry!
I replied using a small Android screen and didn't  take enough care to look at the link itself.
I think I expected it to go to the sticky which does have instructions.

My apologies to the OP.
I will now edit my signature item to make it more useful!

---

### Post by VMC on 2021-01-17
The link below is from Dell and your Inspiron 1150 is listed.[URL="https://www.dell.com/support/kbdoc/en-us/000130686/how-to-troubleshoot-wireless-network-issues-in-ubuntu-linux-on-your-dell-pc"]

How to troubleshoot Dell Wireless network issues[/URL]

---

### Post by asdfsdfgsdfgaefweafersgs on 2021-01-17
Thank you guys so much for the help so far.

so I am in the &#8220;troubleshoot software&#8221; portion of the Dell article and I keep getting &#8220;command not found&#8221; whenever I try this step:


[LIST=1]
[*]Run the following commands:
/etc/pm/config.d/config;
And
SUSPEND_MODULES="<adapter model>"
[/LIST]

---

### Post by VMC on 2021-01-17
Type ```
ls -la /etc/pm/config.d/config
``` from the terminal you have up. I want to see if its executable or even there.
The second command, type ```
env
```, and look for that variable "SUSPEND_MODULES"

---

