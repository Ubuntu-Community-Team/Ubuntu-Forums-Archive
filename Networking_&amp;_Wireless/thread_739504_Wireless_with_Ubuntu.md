---
title: "Wireless with Ubuntu"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by blah569 on 2008-03-29
I have been talking in #ubuntu on irc.freenode.net for a while, and I received some help, but the person that was helping me had to leave.  Anyway, I have found that I have a Realtek (I believe) wireless card, and Ubuntu is not showing the wireless network in the network manager.  I am using Ubuntu 7.10.  I have not installed Ubuntu, so I am running it from the Live CD, as I want to make sure that my wireless will work before I install it.  Any help to get Ubuntu working with a wireless connection would be helpful.  Thanks.

---

### Post by jjgauthi on 2008-03-29
Greetings,

I have had same problem as you, but with the help of the Ubuntu community have managed to get it resolved.

Here is what I have to contribute, if you are using the RTL8185 chipset, which is what I was using.  Then you will first need to go to Realtek and download the windows ME drivers.  In the folder that downloads there is a sub-folder that contains the 98 drivers these are the ones I used to get it to work.  There are two files you will need:

net8185.inf and rtl8185.sys copy these onto a flash drive

next you will need ndiswrapper,  I used the post caled *"RTL8185 fresh install"* the guy there has all the information you will need, follow his simple commands once you have the files and it will work like a charm.  Installing ndiswrapper is easy, once it is on your desktop you will just have to double-click it to install it.

Things to note, place the files on the desktop in a folder all to themselves.  I did all the commands from that folder.  if you  windows it is the same commands to change into a directoy.
[URL="http://becomingamadscientist.blogspot.com/"]
Here[/URL] I have written my notes to myself when I got mine to work, the blog sucks but hey its my notepad.

Things I learned about ndiswrapper, First I tried the XP drivers, they would not work so I had to remove them.  After reading the man page for ndiswrapper I learned:  (I had to learn what a man page was, basicially from what I can gather if you have something installled, on the command line in a terminal type *man item* and it opens a text file that tells you what the item is about)

ndiswrapper - l (Lists the drivers associated or installed with ndiswrapper)
ndiswrapper -r *driver name*lets you remove any invalid drivers

This is about all I can offer look for that post under networkinng and wireless and use the files suggested here and in about five minutes you will have working wireless (well I only know it works on unsecured and WAP security connections no idea about anything else out there).

---

### Post by rMatey on 2008-03-29
I've got a dual boot with Win XP home, and Gutsy Gibon (Ubuntu 7.10) on a Dell B120.  It installed without any problems, and even found the wireless.  It also installed the correct screen resolution but only after I found the right driver.  You'll probably need to do a little looking for yourself, but here are some links that I used to get brave enough to do the install....      My card was a Broadcomm BCM4318 aka Airforce  something or other.or a Dell 1370.  Screen driver was a Dell 900 so I used the Intel driver.
[http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)
[http://tuxmobil.org/](http://tuxmobil.org/)
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)       here on the forums
[http://www.pcworld.com/article/id,130923-c,linux/article.html](http://www.pcworld.com/article/id,130923-c,linux/article.html)

 I found all the information I needed by Googling my particular laptop.  There are so many links out there, I can't really begin to tell you how many.

 One thing I do know, make sure your wireless is on by default in your BIOS.  And the live-CD version didn't necessarily work right off the go for me, either.

---

### Post by blah569 on 2008-03-29
Thanks for the replies.  Would it be easier to just install it on then attempt to get the wireless working as I may have more chances getting wireless working if Ubuntu is already installed?

---

### Post by jjgauthi on 2008-03-29
> **blah569 said:**
> Thanks for the replies.  Would it be easier to just install it on then attempt to get the wireless working as I may have more chances getting wireless working if Ubuntu is already installed?

Well for safety reasons you can do all this on the live cd, it only takes about 5 minutes once you round up all the files.  I tend to just jump in so I blew out my windows and went full bore.  I wouldn't think most persons would do that.

I'd say try it on the live cd, but remember anything you do won't be saved when you reboot so you'll have to redo it.

---

### Post by blah569 on 2008-03-29
My wireless card model is:  RTL8186.  Do you know if that is compatible with Ubuntu 7.10?  (Without having to add any additional drivers, etc) :P

---

### Post by jjgauthi on 2008-03-29
From what I have been reading from the forums and internet there are two answers to your queston (I dont want to sound like an arrogant idiot here so please forgive me)

More than likely your card is compatable but, you might have to do the process some of us went through to get it to work.  By compatable I mean that Ubuntu once you do the workaround will allow you to have network connectivity. 

> **blah569 said:**
> My wireless card model is:  RTL8186.  Do you know if that is compatible with Ubuntu 7.10?  (Without having to add any additional drivers, etc) :P

The best way to check this is to run the live cd.

If you are unsure by what I say there I apologize for confusing you.

[HERE]("http://www.ubuntu.com/getubuntu/download") is a link to the download of 7.10 iso which is the file needed to make a llive cd (a live cd is one that you can boot from without having to install and therefore just run ubuntu as a seperate entity)

[URL="http://www.psychocats.net/ubuntu/iso"]
HERE[/URL] is a link on how to make a cd from the downloaded ISO file

Once you get the cd made, then you can just reboot into Ubuntu and see if your network works right away or not.  If not try the suggestions above but replace the 8185 files with your network card files.

I highly suggest you use your windows 98 drivers, it might take some time to find the correct location if you do a google search.  I spent quite a bit of time but i'm not very computer savy.

I hope this helps.

---

### Post by blah569 on 2008-03-29
> **jjgauthi said:**
> From what I have been reading from the forums and internet there are two answers to your queston (I dont want to sound like an arrogant idiot here so please forgive me)

More than likely your card is compatable but, you might have to do the process some of us went through to get it to work.  By compatable I mean that Ubuntu once you do the workaround will allow you to have network connectivity. 



The best way to check this is to run the live cd.

If you are unsure by what I say there I apologize for confusing you.

[HERE]("http://www.ubuntu.com/getubuntu/download") is a link to the download of 7.10 iso which is the file needed to make a llive cd (a live cd is one that you can boot from without having to install and therefore just run ubuntu as a seperate entity)

[URL="http://www.psychocats.net/ubuntu/iso"]
HERE[/URL] is a link on how to make a cd from the downloaded ISO file

Once you get the cd made, then you can just reboot into Ubuntu and see if your network works right away or not.  If not try the suggestions above but replace the 8185 files with your network card files.

I highly suggest you use your windows 98 drivers, it might take some time to find the correct location if you do a google search.  I spent quite a bit of time but i'm not very computer savy.

I hope this helps.

Thanks for that, but I have used the Live CD countless of times.  On the network manager, I do not see an option for "Wireless Connectivity," too.

---

### Post by jjgauthi on 2008-03-29
> **blah569 said:**
> Thanks for that, but I have used the Live CD countless of times.  On the network manager, I do not see an option for "Wireless Connectivity," too.

Okay that helps, if you are not seeing any wireless network connectivity when you open up the network manager then you would have to try the workaround to get it to work.  Just look a couple of posts up and in about 5 minutes you will find out if you can get it to work or not.

I too did not have the network manager when I first started, so I had to go through alot of pain to get here and I just want to help people not go ballistic like I tend to do.

---

### Post by blah569 on 2008-03-29
> **jjgauthi said:**
> Okay that helps, if you are not seeing any wireless network connectivity when you open up the network manager then you would have to try the workaround to get it to work.  Just look a couple of posts up and in about 5 minutes you will find out if you can get it to work or not.

I too did not have the network manager when I first started, so I had to go through alot of pain to get here and I just want to help people not go ballistic like I tend to do.

Thank you, but I am not exactly sure what kind of posts to look for.

---

### Post by jjgauthi on 2008-03-29
> **blah569 said:**
> Thank you, but I am not exactly sure what kind of posts to look for.

My mistake I'm sorry for being ambiguous, I meant in this thread to look up a few posts I have outlined every step I took to get it working with links to the pertinent sites I got my information from.

I hope this helps.

---

### Post by blah569 on 2008-03-30
> **jjgauthi said:**
> My mistake I'm sorry for being ambiguous, I meant in this thread to look up a few posts I have outlined every step I took to get it working with links to the pertinent sites I got my information from.

I hope this helps.

I have gone to the Realtek site, but all of the files that I have downloaded "The WinME Drivers" do not contain any files even close to what you are mentioning in the 98 subfolder.  Most of them contain two, and they are close to what you stated.

---

### Post by jjgauthi on 2008-03-30
Okay lets see if i can better explain myself, I confuse myself most of the time.

on the realtek site there is the Windows ME download.  When I downloaded that I opened it up in a winzip.  I selected the two INF and SYS files, then extracted those to my desktop.

When they extracted to my desktop they were put in one folder which I opened and it had a windows 98 folder.  In that folder there was a *.inf and a *.sys files I selected I took and put those on a flash drive then put them on my Ubuntu desktop?

If I could figure out how to attach a file I would put them here for you - okay the .sys file is too large, but here is 1/2 of the solution which is hte *.inf file just remove the .txt extension.  the *.sys* file is called rtl8185.sys 

I hope we're starting to cook with gas?

---

### Post by heartburnkid on 2008-03-30
Well, look who's an Ubuntu guru now?  :)

Congratulations jj, nice job getting things working and passing the knowledge along.

---

### Post by jjgauthi on 2008-03-30
I only like posting cause my avatar is so awesomely bad.

---

### Post by blah569 on 2008-03-30
I can not find the RTL8186 driver download on the Realtek site, I can find plenty other models, but not this one.

---

### Post by jjgauthi on 2008-03-30
> **blah569 said:**
> I can not find the RTL8186 driver download on the Realtek site, I can find plenty other models, but not this one.

is that an external wireless card, i looked up a picture on the web and it looks mad crazy.  If so how do you connect it to your computer (cat5 or usb)?  Do you still have the installation disk that came with it?

---

### Post by blah569 on 2008-03-30
> **jjgauthi said:**
> is that an external wireless card, i looked up a picture on the web and it looks mad crazy.  If so how do you connect it to your computer (cat5 or usb)?  Do you still have the installation disk that came with it?

No, it is internal, I believe.

---

### Post by blah569 on 2008-03-30
Sorry to double post, but the card was already on this laptop when I bought it.

---

### Post by smartboyathome on 2008-03-30
I would suggest going with the 8185 drivers. My guess is that they are close enough to work.

---

### Post by jjgauthi on 2008-03-30
I'd have to say in that case then that the 8185 drives might work, its worth a shot.

If that isn't an option i'd send an e-mail to realtek and have them send you the files for that specific card.

---

