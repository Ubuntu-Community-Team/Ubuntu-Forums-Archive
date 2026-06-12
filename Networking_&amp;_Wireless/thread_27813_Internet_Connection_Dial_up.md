---
title: "Internet Connection Dial up"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by Kevin B on 2005-04-17
Hi,
I am new to linux and i have loaded Ubuntu onto a computer. I can not seem to find any way to put in dila up setting to connect to the Internet. I have loaded all the Sever deatils okay.

---

### Post by andvaranaut on 2005-04-17
[QUOTE=Kevin B]Hi,
I am new to linux and i have loaded Ubuntu onto a computer. I can not seem to find any way to put in dila up setting to connect to the Internet. I have loaded all the Sever deatils okay.[/QUOTE]
 Hi Kevin

What you need is called 'ppp'. Your best bet is installing a frontend program to make ppp configuration simple. There are (as far as I know) two graphical frontends to ppp which both work well, one is called 'kppp' and the other is called 'gnome-ppp'. You can install any of them by using the package manager (System > Admin > Synaptic package manager). You will need to enable the universe repository to install gnome-ppp, though.

Once you have installed kppp or gnome-ppp, launch it and you will be able to setup your dialup details.

Please note that if you have an internal modem (a so-called Winmodem) it might be tricky to get it to work, because Winmodem vendors usually don't cooperate much with the Linux community.

Good luck. andvaranaut

---

### Post by andvaranaut on 2005-04-17
Hi Kevin
I was wrong ;) There _is_ a way to configure the dial up connection, and you don't need to install any extra packages.

Try System > Admin > Network. There is an option to configure a modem there.

Best regards

---

### Post by jean on 2005-05-06
Hi ,
  I 'm new to linux too and I had installed ubuntu on  my laptop only a week ago. I'm having a tough time trying to connect to the net using dialup.Here 's what i did:
1) sudo pppconfig
2) Entered all my ISP and user account details (But I'm unable to figure out the Port     
    of my modem,whether it is ttyS1/2/3....or so on )...So i assumed ttyS1!!!
3) sudo pon (I get no error msgs when i did this)
4) sudo poff (Error msg : /usr/bin/poff : No pppd is running .None stopped)

I tried testing my connection after 'sudo pon' by using 'wget',but all got back was an error msg saying 'host not found' .

Can somebody kindly HELLPPP!!!

---

### Post by Professor X on 2005-05-06
Try using wvdial:

```
sudo wvdialconf /etc/wvdial.conf
```

Edit /etc/wvdial.conf so that it contains your ISP phone number, username, and password.

Connect using the command wvdial (Ctrl-C will disconnect).

If this works, then you might want to check out the gnome-ppp app which is a gui for wvdial and is the closest thing to KPPP that gnome has right now.

---

### Post by jean on 2005-05-07
I just tried 'wvdial' but it doesnt detect my modem......it displays the following error msg :
 
Sorry,no modem was detected ! Is it in use by another program?(Ans : NO )  Did you configure it properly with setserial ?(Ans : NO,I didnt!! how do i do that?? )

---

### Post by The_Living_Linux on 2005-05-14
Hi,
   I installed ubuntu 4.10 on my laptop just recently and I was trying to setup my dialup today. Results :  ](*,)  again and again and again.....
I spent a good deal of time going through this forum and listed below are some of the things I tried but didnt work 

1)I tried configuring the dialup through Computer >System Configuration> Networking......but the wizard doesnt recognize my modem...????

2)Wvdial, displays a msg saying "cannot open /dev/modem : no such file or directory"

3)Ran the scanmodem utility and generated the Modem Data.txt file...didnt know what to do then?? :roll: 

I am helplessly lost,what do i do to get my dialup working?

lspci says :
 0000:00:if. 6 Modem : Intel Corp. 82801DB (ICH4) AC'97 Modem Controller (rev 03) 

   Any Kind of help will be much appreciated!!....

   Thanx in advance !!

---

### Post by unisol on 2005-07-14
you have to create a link with the following commands ln -s /dev/ttySx /dev/modem the x is for the port your modem is connected to if you dont know the port, type wvdialconf /etc/wvdial.conf and it should give you the port your modem is on

---

### Post by CameronCalver on 2006-02-24
Hey i have read all the post but when u type in /dev/tty/sx or wateva where do u type it in????

---

### Post by handy on 2006-02-24
The ***_Terminal_***, up on the title bar or panel, of the screen.

**Or:** 

***Menu:* Applications / Accessories / Terminal**

Be careful Cambo! :KS :KS

---

### Post by figtrees on 2006-03-09
Hmm. I went to the Wvdial site. They say that effective with revision 1.50, Wvstreams is needed. I clicked on the link to see what that might be. The first sentence reads, "WvStreams is a network programming library in C++." Does that mean that I must learn to program in C++ before I can connect Ubuntu to the internet through a 56K internal modem? If not, how then is that to be accomplished? Thanks you in advance, George.

---

