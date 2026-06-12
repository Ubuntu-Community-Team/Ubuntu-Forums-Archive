---
title: "Low bandwidth on Ubuntu, Windows box working normally"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by wooz on 2011-02-01
Hey folks,

Finally decided to switch my workstation over from windoze to Ubuntu 10.10.  Loving Ubuntu/Linux.

I have noticed, however, that my internet bandwidth on the ubuntu box is noticeably slower than the windows server I'm usually RDP'd into.  

1) Ubuntu updates... extremely slow.  Sometimes down to 2-3kb.  I have tried several mirrors, some are slightly faster, nothing is magnificent.  I have tried the method in another post of finding the fastest mirror.. not a huge difference.  My ubuntu install at home(about 5km away) is lightning fast.  Sure, we don't have a ton of bandwidth here compared to my apartment(30 users sharing a bonded T), but it shouldn't be this bad.

2) Downloading part 1: I'm currently downloading skype at 2kb.. I tried downloading the same .deb file using my windows box, it is downloading at 70kb.

3) Downloading part 2: I'm downloading the google talk plugin, its going at 1.0kb.  

4) Websites, including this one, load noticeably slower.

This box is a custom from Systemax, brand new.

Edit: I'm also having this problem with an ubuntu 10.10 server on the same network...

Thanks for any assistance you can provide.

---

### Post by cariboo on 2011-02-01
You can check the bandwidth on your internal network using iperf. Iperf is in the repositories, and there are Windows and Mac versions available for free.

Start iperf as a server on one system:

```
iperf -s
```

then on another system as the client:

```
iperf -c <servername>
```

the result should look somehing like this:

Server:

```
cariboo@willy:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.250 port 5001 connected with 192.168.1.215 port 49805
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.1 sec    113 MBytes  93.9 Mbits/sec
```

Client:

```
cariboo@chilanko:~$ iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.215 port 49805 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   113 MBytes  94.5 Mbits/sec
```

I have a 100Mbps network, so the result look OK for me.

Once you've determined your internal network is working properly, you can then chase down who or what is using all your internet bandwidth.

---

### Post by wooz on 2011-02-02
------------------------------------------------------------
Client connecting to fog, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.20 port 52752 connected with 192.168.0.7 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    112 MBytes  94.2 Mbits/sec
root@merlin:/home/wooz# 


Looks good to me

Just ran two Speakeasy speedtests, one from Windows 2003 server(2.15mb down, 2.75mb up)
The other from Ubuntu 10.10 desktop (It was sitting at .15 down, but then it appeared to error out)

Pandora finally loaded after about a half hour of waiting... I actually forgot it was open.  After a few seconds of music, I got: "Your internet connection is slow, causing the music to pause during playback.  Pandora requires at least 64kbps to stream, currently you are getting 23kbps"

Edit: Aaaaand now it gets interesting..!

root@yoda:/home/wooz# scp sympathy.mp3 [email]root@merlin:/home/wooz/sympathy.mp[/email]3
root@merlin's password: 
sympathy.mp3                                  100% 7126KB 142.5KB/s   00:50    
root@yoda:/home/wooz# exit
logout
Connection to yoda closed.
wooz@merlin:~$ scp [email]wooz@yoda:/home/wooz/sympathy.mp[/email]3 ~/symp2.mp3
wooz@yoda's password: 
sympathy.mp3                                    1%  112KB   1.7KB/s 1:10:14 ETA

Yoda is my lucid lynx box at home.  I ssh'd into it from here(merlin, maverick at work) and scp'd sympathy for the devil from yoda to merlin.  This went at 142KB/s and took 50 seconds.
I then tried the reverse, logging out of yoda and executing the command from merlin... it stalled out.

---

### Post by wooz on 2011-02-02
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)

This thread has done wonders for my problem on both boxes.

---

### Post by Mark Phelps on 2011-02-03
An informal benchmark you can do is to access the speedtest.net website in both OSs and compare the results.

If Ubuntu is really a lot slower, other than the MTU hack (which I've personally found to be useless), there's really not much you can do.

The network card/chipset driver is the governing factor and if the one in Ubuntu is not as performant as the one in Windows, you're basically stuck.

---

