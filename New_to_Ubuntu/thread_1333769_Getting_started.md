---
title: "Getting started"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by theronstar on 2009-11-21
Hey, I think once I have crossed this hurdle I can find my feet. I have just installed Ubuntu on another partition. I am using Vista right now. I was wanting to know if all my stuff in Vista will be accessible from Linux, do I need to install my programs over there again.
 
Oh yeah, and how do I activate my internet connection there. Do I need to reconfigure my internet conneciton or is it just something really simple I have overlooked. 
 
Thanks for reading my post.

---

### Post by mörgæs on 2009-11-21
Your windows files will be visible from Ubuntu. In the file manager, you will see a hard drive icon in the menu to the left. This gives access to other partitions.

Ubuntu can not use Windows internet settings. You have to configure this in Ubuntu.

---

### Post by theronstar on 2009-11-21
I use a usb adapter to get at my wireless from downstairs. Will the Network Centre in Linux detect this or will I need to run the installation CD when I have booted up Linux? 
 
Thanks for your help.

---

### Post by samigina on 2009-11-21
1. Your files will be totally accesibles, you will find them in the places menu mainly with the partition name or something like "XXgb drive".

2. Your windows programs will not be there, because Linux is not Windows, is a completely different OS. What programs do you use? Probably you will find that Ubuntu includes all the basic software that someone could need, and office suite, photo editor, web browser, chat, media player, music player..

3. Your connection surely will work out of the box, unless you have a very strange network card,

Welcome!

---

### Post by mörgæs on 2009-11-21
- and regarding Windows applications: In Ubuntu there is access to a _lot_ of good apps. If you really need a Windows app., you can set up a Windows environment inside Ubuntu, but take a look at what is there already. It is likely that you will not need any of your old Windows stuff.

---

### Post by sailthesea on 2009-11-21
Hello and welcome:)
 If your new to Linux/Ubuntu you will have more questions in the near future
Things are rather different from what a Windows user is used to A bit of reading and searching will get you most of the answers you'll need
 As you seem to be mostly up and running you must have a good grasp of the main elements of multi booting
 Linux can read your files in the Windows partition Mount in Nautilus (Linux File Manager) to get them
 Windows Programs will not work in Linux There are no .exe etc You can use Wine or boot into Windows for games and stuff that is not supported There are however many alternatives for Linux that work just as well if not better
 Your internet should be really simple to sort out some hardware is problematic but usually if you open network manager and just look its obvious what you need to do (its on the toolbar little network icon thingy;))
 Good luck and don't be afraid to ask noobish questions Even the very experienced can stumble at first when using a new OS!

 Aargh! Do I really type that slowly?

---

### Post by 3rdalbum on 2009-11-21
Wine only runs a small percentage of Windows programs, so don't have high expectations of it. Find native Linux programs wherever possible. You can find these using Ubuntu Software Center in the Applications menu.

---

### Post by theronstar on 2009-11-21
Hello, I have gone into that network icon in the top right of the ubuntu desktop and entered my SSID and WEP key. It tells me a connection is established but firefox keeps presenting me the page cannot be displayed message when I refresh it. Does anyone have any ideas about what I am doing wrong? 
 
Oh yeah, I am realising I was quite vague when I was asking about programmes I used in Windows and whether I would need them in Linux too. Would I need to download stuff like Java Dev Kit again?

---

### Post by Miljet on 2009-11-21
> Would I need to download stuff like Java Dev Kit again?
The short answer is, yes. Open Synaptic Package Manager (System->Administration->Synaptic Package Manager). Type in your password (the same one you use to login). Click on search at the top of the window and enter "java" in the search box. I think that you will be amazed at the number of different java packages available.

---

### Post by 3rdalbum on 2009-11-21
> **theronstar said:**
> Hello, I have gone into that network icon in the top right of the ubuntu desktop and entered my SSID and WEP key. It tells me a connection is established but firefox keeps presenting me the page cannot be displayed message when I refresh it. Does anyone have any ideas about what I am doing wrong? 

Try manually setting a DNS address for this connection (right-click network manager, go to Edit Connections..., change the properties of the connection you just made, and in the IPv6 and IPv4 settings tabs enter a DNS address).

If you know your ISP's DNS address, then you can happily use that. If you don't know it, then try the OpenDNS addresses:

208.67.222.222
208.67.220.220

---

### Post by theronstar on 2009-11-22
Hello. I did try that but the apply box goes blank when I enter the DNS address. I have spent so long on my Linux today trying to resolve it it is too frustrating. I am going to go back to Vista but thanks for all your help.

---

### Post by mörgæs on 2009-11-22
If you are still reading here: Can you get internet connection with cable?

---

### Post by theronstar on 2009-11-28
Hey, thanks for responding.

I FINALLY got this issue resolved it was so frustrating. Basically there were two drivers that were conflicting and I had to write a blacklist to rt2800usb in a file. Now my wireless works as normal. 

My pc is upstairs and my router is downstairs so I never could have created a wired connection. 

I will mark the thread solved now.

---

