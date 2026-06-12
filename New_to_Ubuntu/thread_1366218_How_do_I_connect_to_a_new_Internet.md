---
title: "How do I connect to a new Internet"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by 0864045 on 2009-12-28
[SIZE=5][COLOR=black]Hi..[/COLOR][/SIZE]
[SIZE=5][/SIZE] 
[SIZE=5][COLOR=navy]Dear brothers:[/COLOR][/SIZE]
[SIZE=5][COLOR=red][/COLOR][/SIZE] 
[SIZE=5][COLOR=red]How do I set up a new telephone connection to the Internet on ubuntu>>?[/COLOR][/SIZE]
[SIZE=5][COLOR=#ff0000][/COLOR][/SIZE] 
[SIZE=5][COLOR=black]Thank you very much..[/COLOR][/SIZE]

---

### Post by lisati on 2009-12-28
No need to start a new thread or to [SIZE="7"]type [COLOR="Olive"]so[/COLOR] [COLOR="Yellow"]large[/COLOR][/SIZE]

---

### Post by okey666 on 2009-12-28
When you say telephone connection, do you mean a dial-up connection or an adsl connection? Do you have a router, or are you using a modem connected directly to your computer?

---

### Post by 0864045 on 2009-12-28
[SIZE=7][COLOR=red]Why>>?[/COLOR][/SIZE]

---

### Post by anewguy on 2009-12-28
That depends.  If you are using an external serial modem, then you should be able to just run pppconfig in a terminal window and use sudo pon to dial out and sudo poff to terminate.

If it's not an external serial modem, things become more complicated.

If you are using an internal modem, please post back the output of this terminal window command:

lspci


If you are using an external USB modem, with the modem plugged in, please post back the output of this terminal window command:

lsusb


External serial modems are the easiest (and fastest, since all of the signal processing, etc., takes place in the modem, not in your PC).  They do not require a driver in Linux.

Internal and USB modems normally require a driver, and that is *IF* one is available for your modems' chipset.

Dave :)

---

### Post by okey666 on 2009-12-28
Could you use the default font instead? It makes it easier to read and it doesn't take up so much screen space.

We need to know how you want to connect to the Internet in order to help you. Do you know what type of connection you have? Is it broadband or dial-up?

Edit:I see from your other thread that you mean dial-up.

---

### Post by 0864045 on 2009-12-28
> **okey666 said:**
> When you say telephone connection, do you mean a dial-up connection or an adsl connection? Do you have a router, or are you using a modem connected directly to your computer?
 
 
[SIZE=4][COLOR=red]I mean Wired Line Phone..[/COLOR][/SIZE]
[SIZE=4][COLOR=#ff0000][/COLOR][/SIZE] 
[SIZE=4][COLOR=#ff0000]Thank you..[/COLOR][/SIZE]
[SIZE=4][COLOR=#ff0000][/COLOR][/SIZE] 
[SIZE=4][COLOR=#ff0000][/COLOR][/SIZE]

---

### Post by okey666 on 2009-12-28
What type of modem do you have? Is in internal (ie. you plug the telephone line into the back of your computer) or external (ie. you plug the telephone line into another machine which you then plug into the computer). If it is an external modem, what type of connection (for example usb) is used to connect it to the computer?

---

### Post by lisati on 2009-12-28
> **0864045 said:**
> [SIZE=7][COLOR=red]Why>>?[/COLOR][/SIZE]

It's hard on the eyes, and you've already asked for help here: [http://ubuntuforums.org/showthread.php?t=1364943](http://ubuntuforums.org/showthread.php?t=1364943)

---

### Post by anewguy on 2009-12-28
BTW - it is respectful on most forums, including this one, to use the default font and font color.  Anything other than that is normally considered the equivalent of shouting, and is taken as rather rude.  Please do use only the default font and font color.

Dave :)

---

### Post by 0864045 on 2009-12-28
[SIZE=3]I thank all those who responded

[/SIZE][SIZE=3]But you did not understand what I mean or I have not brought the bit of information in the correct format

[/SIZE][SIZE=3]I was working on Windows and there was an option in the Control Panel name: Network Connections if you come by the name option: Create a new connection

[COLOR=navy]My question is: Where is the location of these options in ubuntu..?[/COLOR][/SIZE]
[SIZE=3][COLOR=#000080][/COLOR][/SIZE] 
[SIZE=3][COLOR=#000080][/COLOR][/SIZE] 
[SIZE=3][COLOR=#000080][/COLOR][/SIZE]

---

### Post by 0864045 on 2009-12-28
> **anewguy said:**
> BTW - it is respectful on most forums, including this one, to use the default font and font color. Anything other than that is normally considered the equivalent of shouting, and is taken as rather rude. Please do use only the default font and font color.
 
Dave :)
 
 
[SIZE=1]I'm sorry I did not know that this disturbs you[/SIZE]

---

### Post by okey666 on 2009-12-28
As I find it hard to explain the location of icons I have attached a screen shot with it circled.

If you right click on this icon and then click on edit connections it will allow you to make new connections. However, dial-up connections can be tricky in Ubuntu as support has not been focused on them.

---

### Post by 0864045 on 2009-12-28
> **okey666 said:**
> As I find it hard to explain the location of icons I have attached a screen shot with it circled.
 
If you right click on this icon and then click on edit connections it will allow you to make new connections. However, dial-up connections can be tricky in Ubuntu as support has not been focused on them.
 
[SIZE=1]Is not there a certain way of applications..?[/SIZE]

---

### Post by mlentink on 2009-12-28
> **0864045 said:**
> [SIZE=1]Is not there a certain way of applications..?[/SIZE]


In the other thread I have already explained to you that this ***is*** the application comparable to the Windows Network Connections.

Have you already tried using it? If so, what problems did you encounter?

Please stick to one thread only and try to explain as clearly as you can what you have done so far and what went wrong. It will make it easier for us to help you.

Also, I suppose English is not your native language. You might want to try and find a forum that is in your native tongue. Take a look here: [http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

---

### Post by 0864045 on 2009-12-28
> **mlentink said:**
> In the other thread I have already explained to you that this ***is*** the application comparable to the Windows Network Connections.
 
Have you already tried using it? If so, what problems did you encounter?
 
Please stick to one thread only and try to explain as clearly as you can what you have done so far and what went wrong. It will make it easier for us to help you.
 
Also, I suppose English is not your native language. You might want to try and find a forum that is in your native tongue. Take a look here: [http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)
 
 
Thank you..

---

### Post by steveneddy on 2009-12-28
I propose merging this with the other thread or deleting this thread because this thread does nothing but reference to the other thread.

---

### Post by mlentink on 2009-12-28
> **steveneddy said:**
> i propose merging this with the other thread or deleting this thread because this thread does nothing but reference to the other thread.
+1

---

### Post by anewguy on 2009-12-29
If you want to set up a dial up connection, run pppconfig from a terminal window (applications/accessories/terminal):

sudo pppconfig <press enter>

It will ask for things like the number you want to dial, your username, password, etc., just like setting up a dial up connection in Windows.  Note that by default it seems to be going to ttyS1, when in my case my serial modem is connected on ttyS0 (com1). As I mentioned before, if your modem is internal or connected via USB, follow my previous post and paste the information back here as you WILL need a driver for your modem, *IF* one is available.

When everything is set up and you *know* you can "talk" to your modem, open a terminal window (applications/accessories/terminal) and type:

sudo pon <press enter>


To disconnect, just do:

sudo poff <press enter>


Everyone here understands what you want to do, but we need you to understand that we are giving you the tools available and you need to try them.  We also need the information on modem type, manufacturer and model.

Dave :)

---

### Post by 0864045 on 2009-12-30
> **anewguy said:**
> If you want to set up a dial up connection, run pppconfig from a terminal window (applications/accessories/terminal):
 
sudo pppconfig <press enter>
 
It will ask for things like the number you want to dial, your username, password, etc., just like setting up a dial up connection in Windows. Note that by default it seems to be going to ttyS1, when in my case my serial modem is connected on ttyS0 (com1). As I mentioned before, if your modem is internal or connected via USB, follow my previous post and paste the information back here as you WILL need a driver for your modem, *IF* one is available.
 
When everything is set up and you *know* you can "talk" to your modem, open a terminal window (applications/accessories/terminal) and type:
 
sudo pon <press enter>
 
 
To disconnect, just do:
 
sudo poff <press enter>
 
 
Everyone here understands what you want to do, but we need you to understand that we are giving you the tools available and you need to try them. We also need the information on modem type, manufacturer and model.
 
Dave :)
 
 
 
 
[SIZE=2]Thank you very much for your interaction that the answer that I want[/SIZE]

---

### Post by anewguy on 2009-12-30
Please let us know how this works for you, and if you need a modem driver.

Dave :)

---

### Post by 0864045 on 2010-01-09
> **anewguy said:**
> Please let us know how this works for you, and if you need a modem driver.
 
Dave :)
 
 
 
[SIZE=3]The first thing we do is go to the list[/SIZE]
 
[CENTER][FONT=Times New Roman][SIZE=4]System > Preferences > Network Connection[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4][IMG]http://img691.imageshack.us/img691/193/sanstitre10.jpg[/IMG][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4][IMG]http://img21.imageshack.us/img21/5128/sansjjtitre.png[/IMG][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5][SIZE=3]Then go to tab DSL and then put pressure on the[/SIZE] [SIZE=3]ADD[/SIZE][/SIZE][/FONT][FONT=Times New Roman][SIZE=4][IMG]http://img269.imageshack.us/img269/9720/sanstitre11a.jpg[/IMG][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4][IMG]http://img21.imageshack.us/img21/5128/sansjjtitre.png[/IMG][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]And then fill in the boxes do what is necessary, as shown in the picture[/SIZE][/FONT][FONT=Times New Roman][SIZE=4][IMG]http://img41.imageshack.us/img41/9240/sanstitre12dr.jpg[/IMG][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4][IMG]http://img21.imageshack.us/img21/5128/sansjjtitre.png[/IMG][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Contacts Send order to go to run the vacuum to the upper connection icon, and press it and choose Contact
You want to use it as in the picture[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I brought you the answer to my question with pictures..:D[/SIZE][/FONT][/CENTER]

---

