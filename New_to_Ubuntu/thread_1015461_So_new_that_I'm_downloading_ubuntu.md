---
title: "So new that I'm downloading ubuntu"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Secretblend on 2008-12-18
Hello all, I am Secretblend and I'm gonna try out Ubuntu. I have couple of questions and I hope some of you would answer.

My first question is about drivers. 

How would I find drivers or do I even have to find them? What can I expect when first starting to load ubuntu. Please keep it very simple and I'm sure I'll have more questions as I go deeper.

To start, I have 

Intel DG45ID Media Series motherboard with duo processor.

4 gig memory.

Thanks.

---

### Post by drs305 on 2008-12-18
Welcome to ubuntu Secretblend.

It's easy. Load it up and see what doesn't work. Hopefully everything will work for you out of the box. 

Once you have it installed you can go to Main Menu, System, Administration, Hardware Drivers to see if ubuntu has detected drivers that may be available for activation.

There isn't too much you have to do beforehand - just let ubuntu have at it and see what kind of job it does installing things.

If you have particular concerns you can do a forum search for your specific hardware to see if there have been any issues.

---

### Post by hayden92 on 2008-12-18
Well, generally Ubuntu searches for the appropriate drivers and utilises them automatically. To see the drivers that are currently in use: click on "System", then "Hardware Drivers" and the interface is pretty straightforward.
Also, I'm pretty sure that Ubuntu will notify if it wants to install new or proprietary drivers.


You should post all of your questions so that we can have a go at answering the rest of them.

Hope that helps
Hayden

---

### Post by Secretblend on 2008-12-18
Thanks for the reply. If I do end up needing drivers, where would I go to get them?

I am sure I will have plenty of questions as I dive deeper into ubuntu.  

I guess after reading the 2 replies, My next question should be, Can I install ubuntu on harddrive that already has windows on it? I obviously am not ready to get rid of my Vista yet.

---

### Post by mkvnmtr on 2008-12-18
Most drivers you will need are part of the Kernal. If there are one or two that are not open source they will probably be listed in system>hardware drivers. Mostly you just have to enable them and they will be downloaded and installed. But sometimes what is provided does not work for someones machine. Then they have to come to the forum to find a work around.For most equipment it is not too hard. But for most folks it just works out of the box. You will be able to tell better when you have the live disk.

---

### Post by drs305 on 2008-12-18
You might want to try wubi, which installs ubuntu as a file within Windows. You use the Windows boot loader to access it and you can see if you like it. You can even access it while you are running windows. And to uninstall it you simply use window's Add/Remove program.
Here is some information: 
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Ubuntu?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Ubuntu?")
[URL="http://en.wikipedia.org
/wiki/Wubi_(Ubuntu)"]http://en.wikipedia.org/wiki/Wubi_(Ubuntu)[/URL]


Of course, you can also just try the LiveCD without installing anything permanently.

---

### Post by newbee70 on 2008-12-18
> **Secretblend said:**
> Thanks for the reply. If I do end up needing drivers, where would I go to get them?

I am sure I will have plenty of questions as I dive deeper into ubuntu.  

I guess after reading the 2 replies, My next question should be, Can I install ubuntu on harddrive that already has windows on it? I obviously am not ready to get rid of my Vista yet.

Welcome to the forums,

spend some time going through the requests for help, you can learn quite a bit about how to troubleshoot many problems you might face.

---

### Post by donkyhotay on 2008-12-18
Depending on your hardware things either work perfectly without needing to do much, or they don't which can sometimes be a problem (as you'll notice browsing through this forum). Once you get it working, see what does/doesn't work. Anything you have problem a with post online here and we'll try to help you out.

---

### Post by Secretblend on 2008-12-19
Thanks for the reply everybody. So far I like it. I have to say I'm amazed how good it has worked. I haven't had to install any drivers and it all seems to be working. However, I've noticed coupl of things that I'll have to play with when I have time.
 
One is that I tried to set up hotmail using the mail program and I have to say I'm kinda sad that I have to set that up instead of having it work since I thought hotmail was popular. However that is not a big deal.

Other thing I've noticed is the volume control. I have to have it as high as possible in order to hear it and even then I had to turn up the volume on speakers too. Is there a way to adjust it so that I can hear it well in middle setting instead of all the way up?

Other problem I had was I tried to run a DVD. I put in one to test and see how it works and it kept saying it needs a decoder of some sort, I forget the name. I downloaded what it recommened and it still didnt' work.

---

### Post by sneeks on 2008-12-19
hi there,we will start with the first one,hotmail is normally an online mail service,so r u trying to get it to run with a mail client like Thunderbird ?
as for playing your dvd's,yes you do need the codecs,which you can find in the repositories,or synaptic package manager.
if you install the g streamer bad and ugly packages that will normally do it.

---

### Post by donkyhotay on 2008-12-19
For the volume issue install alsamixergui
```
sudo apt-get install alsamixergui
```
which is a very useful GUI program that allows you to customize all of your various sound input/outputs.

---

### Post by laurielegit on 2008-12-19
OK your dvd problem comes down to two things. You may either need to install the ubuntu restricted extras or your dvds may be encrypted. If the first is correct you just need to go to Applications --> Add/Remove Programs, select "All available software" and searching for "Ubuntu Restricted Extras". This will install dvd support, flash, java and many other codecs and suchlike. If your dvds are encrypted though, you have a larger task. Here is the method:
> 
The movie players provided in Ubuntu can play back unencrypted DVDs. However, many commercial DVDs are encrypted with a weak algorithm called Content Scrambling System (CSS).You can enable playback of encrypted DVDs with MPlayer, xine and Totem-xine by installing libdvdcss2.

The CSS key sets are licensed to manufacturers who incorporate them into products such as DVD drives, DVD players and DVD movie releases.Most DVD players are equipped with a CSS Decryption module.

**_Installing libdvdcss2_**

First you need to install the libdvdread3 package using the following command

sudo apt-get install libdvdread3

Now download the libdvdcss2 library using the following command

sudo /usr/share/doc/libdvdread3/install-css.sh
[B][U]
For AMD64 Users[/U][/B]

First you need to install the following packages

sudo apt-get install debhelper build-essential fakeroot

Now download the libdvdcss2 library using the following command

sudo /usr/share/doc/libdvdread3/install-css.sh


That’s it now Your DVD player should now play back encrypted DVDs.You can ope your Movie player from Applications > Sound & Video 

The commands you see should be copied into terminal. This can be accessed from Applications -->Accessories --->Terminal

Best of luck,

Laurie

---

### Post by Secretblend on 2008-12-19
> **sneeks said:**
> hi there,we will start with the first one,hotmail is normally an online mail service,so r u trying to get it to run with a mail client like Thunderbird ?
as for playing your dvd's,yes you do need the codecs,which you can find in the repositories,or synaptic package manager.
if you install the g streamer bad and ugly packages that will normally do it.

I was trying to use what came with ubuntu which is Evolution. Is that a good one or should I find another like Thunderbird?

---

### Post by donkyhotay on 2008-12-19
Evolution is essentially outlook for linux. Not outlook express but the full outlook complete with Email, contacts, calendar, etc. Because of this I find evolution to be pretty bulky and slow compared to thunderbird. On the other hand thunderbird doesn't do all of the extra stuff that evolution does. My suggestion is if you just need Email to use thunderbird. But if you need all the other things evolution comes with then definitely use it instead.

---

