---
title: "Please Help: Modem is Ultra-Slow in Ubuntu"
date: 2005-03-27
forum: Networking &amp; Wireless
---

### Post by Tet Omeg on 2005-03-27
Hello, I hope someone here can help me solve this problem.

My dial-up internet connection is very slow in Ubuntu: it averages around 800 bytes per second in Ubuntu. Whereas using the same internet service provider, phone line and account on two other computers (one is running Windows XP and the other is running Windows 98 SE) gets an average of around 4.5 kilobytes per second. The computer running Windows 98 SE actually uses the external modem that I'm using on my computer running Ubuntu (of course, after I disconnect it and reconnect it from one computer to the other).

The modem I'm using in Ubuntu is a Multi-Tech MT5600ZDX external modem. The computer I'm running Ubuntu on is a Pentium III Dell Dimension 4100. The modem is connected to the computer at the COM1 serial port via a 9-pin serial cable, which connects to the modem via a 9-pin to 25-pin (i.e., RS232) port adapter (this is the exact same modem and set-up that I'm using on an old Pentium II Compaq Presario 4824 running Windows 98 SE, and it works just fine there).

A funny thing about it is that I've noticed that the download rate can sometimes reach 5 kilobytes per second or even more in Ubuntu using this set-up, but it only will last for a few seconds like that. Around 800 bytes per second is about the average (sometimes much less, sometimes a little more). I find this odd because it tells me that it's capable of achieving reasonable download rates, but for whatever reason it won't stick with it.

I know the modem itself is working just fine, because when I hook up this same modem in the same manner to an old Pentium II Compaq Presario 4824 running Windows 98 SE, it works just fine there. And I know it's not a random fluke with my internet service provider having had problems while I happened to be using Ubuntu, as I've been testing this back and forth between these three different computers for three days now, and the results are always the same.

Below are the Network Settings for this modem in Ubuntu:

Device: ppp0
Modem port: /dev/ttyS0

The Pentium III Dell Dimension 4100 that I'm running Ubuntu on also has an internel PCI winmodem: a 56 kilobits per second Conexant HCF modem. This is going unused as it requires a proprietary and payware driver from Linuxant to be able to use it in Linux.

I would be most appreciative of any help anyone can offer me on this matter.

---

### Post by smarttaz on 2005-03-27
I THOUGHT I have the same problem under Ubuntu 4.10 myself, and I compared the performance of my external hardware modem [http://www.trendnet.com/products/TFM-560X.htm](http://www.trendnet.com/products/TFM-560X.htm) with its results on the same machine, but under Slackware 10.1.

However, you can't rely much on the speed shown (or not!) by gnome-ppp (or kppp on other distros).

Download with 'wget' a large file from a site with good connection, like [ftp://ftp.belnet.be](ftp://ftp.belnet.be), and watch the average speed to have a good estimate.

Or, use the following quick tests:

1. [http://www.linternaute.com/vitesse/](http://www.linternaute.com/vitesse/)
I got with my 56K modem (connected at 115200 by wvdial):
UBUNTU == 35...42 kbps (4.4...5.2 KBytes/s)
Slack == up to 137...140 kbps (17...18 KBytes/s), with HW compression

2. [http://specials.zdnet.co.uk/misc/band-test/speedtest.html](http://specials.zdnet.co.uk/misc/band-test/speedtest.html)
I got with my 56K modem (connected at 115200):
UBUNTU == ~46 kbps ( 5.6-5.7 KBytes/s)
Slack== ~45.5 kbps (5.6 KBytes/s)

3. [http://reviews.cnet.com/Bandwidth_meter/7004-7254_7-0.html](http://reviews.cnet.com/Bandwidth_meter/7004-7254_7-0.html)
I got with my 56K modem (connected at 115200):
UBUNTU == ~ 41.6 kbps (5.2 KBytes/s)
Slack== ~ 42 kbps (5.2 KBytes/s)

Is your modem connecting @ 115200, as a decent 56K modem should think it can do? (with HW compression) 
Maybe you should check your connection settings ('sudo pppconfig' or, if you use wvdial, check the wvdial.conf file)

The only part where Slackware managed to automatically configure my modem better was the fact that actually with slack's connection strings, my modem always managed to negociate a compressed connection (115200) with my ISP's modem, so for compressable files I could get even 140 kbps for some 30 continuous seconds!! (of course, NOT tar.gz nor tar.bz2 files, but regular files were transferred with HW compression)

Now, under Ubuntu, it seems it can't negociate a compression during the connexion...

R.

---

### Post by e_machinist on 2005-03-27
This seems to be a fairly common occurence with External Serial modems when you use the gnome-nettools (Computer>System Configuration>Networking). The problem is that the nettools never seems to allow the modem to operate at full speed.

To fix it you should forget nettools and just use wvdial to connect to the internet.

First you need to run in a terminal: sudo wvdialconf location of the wvdial.config file. This will run through the autodetection process for the modem and set the Default settings for it when wvdial dials. wvdial should set it's speed at 115200.

The wvdial config file is usually located in /usr/bin and /etc.

So you could try: sudo wvdialconf /usr/bin/wvdial.conf

That would output to the possibly correct place for your configuration. If not then try writing the file output to the other locations that wvdialconf is reported at. Use: whereis wvdialconf or whereis wvdial.conf to find the file from a terminal.

After you have saved the wvdialconf settings to the correct place or mutliple correct places you need to edit wvdial.conf, so pico or gedit your way there as in: sudo pico /usr/bin/wvdial.conf

You should see three spots with ";" preceeding a number to dial, username and password fields. Delete the three ; ; ;, and put in your information.

Save that file. Now run wvdial: sudo wvdial

wvdial should take over after you enter your system password and dial up. Hopefully you have a fast connection now.

Also, should leave the terminal window open that has your active connection in it using wvdial so that when you want to disconnect you should press Ctrl + C. This will close the connection and wvdial will give you some feedback on the disconnect process.

Good luck.
E

---

### Post by Tet Omeg on 2005-03-27
[QUOTE=e_machinist]This seems to be a fairly common occurence with External Serial modems when you use the gnome-nettools (Computer>System Configuration>Networking). The problem is that the nettools never seems to allow the modem to operate at full speed.

To fix it you should forget nettools and just use wvdial to connect to the internet.

First you need to run in a terminal: sudo wvdialconf location of the wvdial.config file. This will run through the autodetection process for the modem and set the Default settings for it when wvdial dials. wvdial should set it's speed at 115200.

The wvdial config file is usually located in /usr/bin and /etc.

So you could try: sudo wvdialconf /usr/bin/wvdial.conf

That would output to the possibly correct place for your configuration. If not then try writing the file output to the other locations that wvdialconf is reported at. Use: whereis wvdialconf or whereis wvdial.conf to find the file from a terminal.

After you have saved the wvdialconf settings to the correct place or mutliple correct places you need to edit wvdial.conf, so pico or gedit your way there as in: sudo pico /usr/bin/wvdial.conf

You should see three spots with ";" preceeding a number to dial, username and password fields. Delete the three ; ; ;, and put in your information.

Save that file. Now run wvdial: sudo wvdial

wvdial should take over after you enter your system password and dial up. Hopefully you have a fast connection now.

Also, should leave the terminal window open that has your active connection in it using wvdial so that when you want to disconnect you should press Ctrl + C. This will close the connection and wvdial will give you some feedback on the disconnect process.

Good luck.
E[/QUOTE]

That solved the speed problem. Thank you very much.

Now I have a different problem that I hope someone here can help me solve:

Recently I'm finding it quite impossible to connect to the website [http://www.anti-state.com](http://www.anti-state.com) in Ubuntu. I can connect to that website just fine from a different computer running Windows XP and Opera.

What is even more weird about this is that I was able to connect to that website in Ubuntu a bit over day or so ago (i.e., even with the ultra-slow speed issue I was having), but ever since about last night I haven't been able to connect to that website (i.e., even before the speed issue had been solved).

Like I said, I'm having no trouble whatsoever connecting to that website using a different computer running Windows XP and Opera. I've been testing this back and forth between computers so I know it's not just some random fluke wherein I happened to catch a time when anti-state.com's server was busy or down.

What I can see happening (while running Ubuntu) is that Firefox will say "Resolving host www.anti-state.com" and then very quickly after that it will say "Connecting to www.anti-state.com," but then nothing whatsoever happens after that. From the lights on my external modem I can see that no data is being transferred after it says "Connecting to www.anti-state.com" (other than a few quick blips every now and then, as if it's trying to establish a connection but isn't able to). It doesn't matter how long I wait, no data is ever transferred.

This is the only website of all that I have tried wherein I am having this problem.

Again, I would be very appreciative of any help anyone can offer me to help me solve this problem.

---

### Post by Tet Omeg on 2005-03-28
[QUOTE=Tet Omeg]...

Now I have a different problem that I hope someone here can help me solve:

Recently I'm finding it quite impossible to connect to the website [http://www.anti-state.com](http://www.anti-state.com) in Ubuntu. I can connect to that website just fine from a different computer running Windows XP and Opera.

What is even more weird about this is that I was able to connect to that website in Ubuntu a bit over day or so ago (i.e., even with the ultra-slow speed issue I was having), but ever since about last night I haven't been able to connect to that website (i.e., even before the speed issue had been solved).

Like I said, I'm having no trouble whatsoever connecting to that website using a different computer running Windows XP and Opera. I've been testing this back and forth between computers so I know it's not just some random fluke wherein I happened to catch a time when anti-state.com's server was busy or down.

What I can see happening (while running Ubuntu) is that Firefox will say "Resolving host www.anti-state.com" and then very quickly after that it will say "Connecting to www.anti-state.com," but then nothing whatsoever happens after that. From the lights on my external modem I can see that no data is being transferred after it says "Connecting to www.anti-state.com" (other than a few quick blips every now and then, as if it's trying to establish a connection but isn't able to). It doesn't matter how long I wait, no data is ever transferred.

This is the only website of all that I have tried wherein I am having this problem.

Again, I would be very appreciative of any help anyone can offer me to help me solve this problem.[/QUOTE]

I installed the Opera 7.54u2 browser on Ubuntu and it's having this same problem. The progress bar in Opera shows absolutely no data-transfer from the [http://www.anti-state.com](http://www.anti-state.com) website--not so much as a single byte.

Yet I have absolutely no problem accessing this website under Windows XP with either Opera, K-Meleon, or Maxthon.

And I have no problems accessing any other websites in Ubuntu using either Firefox or Opera. It's only this one website which is apparently blocked.

Like I said, I was accessing this website in Ubuntu using Firefox more than a day ago even when I was having the ultra-slow speed problem.

Please, if anyone can help me with this problem I would be very grateful.

---

### Post by Tet Omeg on 2005-03-28
[QUOTE=Tet Omeg]I installed the Opera 7.54u2 browser on Ubuntu and it's having this same problem. The progress bar in Opera shows absolutely no data-transfer from the [http://www.anti-state.com](http://www.anti-state.com) website--not so much as a single byte.

Yet I have absolutely no problem accessing this website under Windows XP with either Opera, K-Meleon, or Maxthon.

And I have no problems accessing any other websites in Ubuntu using either Firefox or Opera. It's only this one website which is apparently blocked.

Like I said, I was accessing this website in Ubuntu using Firefox more than a day ago even when I was having the ultra-slow speed problem.

Please, if anyone can help me with this problem I would be very grateful.[/QUOTE]

I did a ping on [www.anti-state.com](www.anti-state.com) and below is what the Terminal produced:

$ ping [www.anti-state.com](www.anti-state.com)
PING anti-state.com (72.3.135.33) 56(84) bytes of data.
64 bytes from antiwar.com (72.3.135.33): icmp_seq=1 ttl=49 time=205 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=2 ttl=49 time=161 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=3 ttl=49 time=174 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=4 ttl=49 time=168 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=5 ttl=49 time=164 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=6 ttl=49 time=161 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=7 ttl=49 time=221 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=8 ttl=49 time=168 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=9 ttl=49 time=209 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=10 ttl=49 time=149 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=11 ttl=49 time=206 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=12 ttl=49 time=156 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=13 ttl=49 time=211 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=14 ttl=49 time=176 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=15 ttl=49 time=171 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=16 ttl=49 time=158 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=17 ttl=49 time=216 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=18 ttl=49 time=160 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=19 ttl=49 time=209 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=20 ttl=49 time=161 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=21 ttl=49 time=205 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=22 ttl=49 time=152 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=23 ttl=49 time=208 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=24 ttl=49 time=169 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=25 ttl=49 time=215 ms

...

And it just kept on going on like that. I shut it down when the "icmp_seq=" was up above 200.

Does anyone have any ideas as to what is going on? Please, like I said, if anyone can help me with this problem I would be very grateful.

---

### Post by Tet Omeg on 2005-03-28
[QUOTE=Tet Omeg]I did a ping on [www.anti-state.com](www.anti-state.com) and below is what the Terminal produced:

$ ping [www.anti-state.com](www.anti-state.com)
PING anti-state.com (72.3.135.33) 56(84) bytes of data.
64 bytes from antiwar.com (72.3.135.33): icmp_seq=1 ttl=49 time=205 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=2 ttl=49 time=161 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=3 ttl=49 time=174 ms
...

...

And it just kept on going on like that. I shut it down when the "icmp_seq=" was up above 200.

Does anyone have any ideas as to what is going on? Please, like I said, if anyone can help me with this problem I would be very grateful.[/QUOTE]

I am also unable to connect to [http://www.antiwar.com](http://www.antiwar.com) , [http://www.somalianarchy.com](http://www.somalianarchy.com) , and [http://www.foranewliberty.com](http://www.foranewliberty.com) . They all have the same IP address: 72.3.135.33 .

I did a Wget on these websites, and below is the result:

$ wget [http://www.anti-state.com/index.php](http://www.anti-state.com/index.php)
--18:34:17--  [http://www.anti-state.com/index.php](http://www.anti-state.com/index.php)
          => `index.php'
Resolving [www.anti-state.com](www.anti-state.com)... 72.3.135.33
Connecting to [www.anti-state.com](www.anti-state.com)[72.3.135.33]:80...

-------

It produces the same result for [http://www.anti-state.com/forum/index.php](http://www.anti-state.com/forum/index.php) , [http://www.antiwar.com](http://www.antiwar.com) , [http://www.somalianarchy.com](http://www.somalianarchy.com) , and [http://www.foranewliberty.com](http://www.foranewliberty.com) . It just gets to "Connecting to" and nothing else ever happens.

Please, any help anyone can offer me I would be very appreciative.

---

