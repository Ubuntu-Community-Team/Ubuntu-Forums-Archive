---
title: "Inspiron 1525, no wifi recognition"
date: 2019-09-06
forum: Networking &amp; Wireless
---

### Post by zetomes on 2019-09-06
Greetings all and thanks for your patience and attention,

Here it goes:

lubuntu version installed: 18.04 LTS
computer: Inspiron 1525


For a few times I installed some Lubuntu versions on different computers, some installations were tough bones, some were very easy, but I never got stuck like this. I&#8217;m not a programmer nor I know Linux language, I&#8217;m just a curious using experience as my tool. 


I tried to install many different Lubuntu versions on a friend&#8217;s computer whose Windows got outdated, but without success. The combination of the version installed presently (18.04 LTS) and the present partitioning scheme resulted in a partial success but, I can&#8217;t put the wireless working (it doesn't recognize the drives I think), it takes some time starting up and shutting down with large messages of error, and also it takes a few time after hibernation. 

I don&#8217;t know if I partitioned the hard disk correctly, if 18.04 LTS is the proper Lubuntu version (from all the other versions installed this is the one with most success), if there's a problem because the battery isn't working... but the greatest problem continues to be the wireless. This is my last hope&#8230;, before I take the computer to a computer store and spent some money.


I'm not sure If I uploaded the imagens regarding the partitioning and the info report...


Many thanks in advance

PS: how do I upload files (regarding the hardware, system info and the images of the partitioning)?

---

### Post by wildmanne39 on 2019-09-06
Hello and welcome to the forum!

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will most likely be able to help.

---

### Post by zetomes on 2019-09-06
Greetings, and thanks!
I'm afraid for the moment I don't have access to a wired connection... :(
The computer I'm using is working perfectly with wifi and it's not the one with the problems...

---

### Post by wildmanne39 on 2019-09-06
You do not need a wired connection in the link are directions for running the script without internet, however you can also tether your cell phone to your computer and use it as a wired connection, if your cell phone can be used as a hotspot.

---

### Post by zetomes on 2019-09-06
Thanks!
I followed the instructions:

[SIZE=4][COLOR=#000000][COLOR=DarkRed]**Method 2. No Internet - GUI Method (multi-step but still easy to do :smile:)-**[/COLOR][/COLOR][/SIZE]

[COLOR=#000000]If you can't connect to internet -[/COLOR]

[COLOR=#000000]* Download the script on another computer by right-clicking [/COLOR][this link]("https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info")[COLOR=#000000], and choose to "Save" the link target.[/COLOR]
[COLOR=#000000]* [/COLOR][B]Copy the downloaded file to your Ubuntu Desktop (see the "NOTE 2" below) and,
* run it from there as follows -

**1)** Right-click the downloaded file > click "Properties" > go to "Permissions" tab > tick the "Execute" checkbox > close the box.

**2)** Double-click the file > select "**Run**" in the opened dialogue box. Provide your password when asked.
[I][COLOR=#800000][**NOTE 1:** Since Ubuntu 13.04, Text Files open up in text editor even if they are made executable. To change this-
Open any folder > go to **Files > Preferences > Behavior tab > select "Ask each time"** option under "Executable Text Files" section.]
[/COLOR][/I]... 

but nothing happened.
there was no generated file, and the size of the file "wireless-info.txt" kept the same. When I executed it in the terminal the size of the file increased and the only visible text was "#### wireless info START ####". The partition where the file was run (/home/user) is a Linux Ext4... Perhaps I'm not interpreting the instructions correctly...


[/B]

---

### Post by zetomes on 2019-09-06
Persistence won.

I executed the file "wireless_script.txt" next to the "wireless-info.txt" file and voila, it modified it!

Here it goes!

[http://pastebin.ubuntu.com/p/3nsBgxGkxN/](http://pastebin.ubuntu.com/p/3nsBgxGkxN/)

---

### Post by chili555 on 2019-09-06
You need firmware. Post #11 here shows you the process. [https://ubuntuforums.org/showthread.php?t=2361632&p=13646580#post13646580](https://ubuntuforums.org/showthread.php?t=2361632&p=13646580#post13646580)

---

### Post by zetomes on 2019-09-07
You guys are simply... fantastic!

Wireless is working perfectly!
At this moment updating the system.

How can I send a report of the computer to see if the problems I mentioned initially persist and a map of the partitioning?

Huge and sincere thanks [wildmanne39]("http://ubuntuforums.org/member.php?u=508533"), [chili555]("https://ubuntuforums.org/member.php?u=35909")[COLOR=#000000],[/COLOR] really.

---

### Post by zetomes on 2019-09-07
Shall I create a new topic for my other issues?

---

### Post by chili555 on 2019-09-07
> **zetomes said:**
> Shall I create a new topic for my other issues?
Yes, please, in the appropriate section, probably General.

---

### Post by zetomes on 2019-09-07
ok, thanks!

---

### Post by prabodh03 on 2019-09-14
Thanks for the hack man, was facing the same issue but things have resolved now.


> **zetomes said:**
> Persistence won.

I executed the file "wireless_script.txt" next to the "wireless-info.txt" file and voila, it modified it!

Here it goes!

[http://pastebin.ubuntu.com/p/3nsBgxGkxN/](http://pastebin.ubuntu.com/p/3nsBgxGkxN/)

---

### Post by prabodh03 on 2019-09-14
Just installing the drivers for the wifi adapter solved the issue for me, thanks a lot.

> **chili555 said:**
> You need firmware. Post #11 here shows you the process. [https://ubunt instauforums.org/showthread.php?t=2361632&p=13646580#post13646580]("https://ubuntuforums.org/showthread.php?t=2361632&p=13646580#post13646580")

---

