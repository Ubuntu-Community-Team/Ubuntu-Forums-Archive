---
title: "ftp and UFW issues"
date: 2015-11-12
forum: Networking &amp; Wireless
---

### Post by steve234 on 2015-11-12
Firstly - I am aware that ssh and sftp exist - I use them between my Mac & my Android device. What I'm trying to acheive here is a quick and dirty solution for file transfer on my home network using my netbook (running Lubuntu) - without having to disable ufw. 

I'd basically rather use ftp + put from the cli than buy a bluetooth adaptor for my old netbook. I can open an ftp server on my Android device with one tap - because it is built in to a file manager. I have no idea how to start an ssh server on that device.

If ufw is disabled - all is good ftp wise - I can get and put files to my heart's content.

If ufw is running then the connection times out. 

I've now made a dog's breakfast of my UFW rules by trying solutions offered by various tutorials. This is a hard topic to research as the standard answer is "use ssh".

My iptables rules include these:  (where **** is the port number for the ftp server on my adroid device)


21/tcp                     ALLOW       Anywhere****                      ALLOW       Anywhere
****/tcp                   ALLOW       Anywhere
****/udp                   ALLOW       Anywhere
21                         ALLOW       Anywhere
22                         ALLOW       Anywhere


**** (v6)                  ALLOW       Anywhere (v6)****/tcp (v6)              ALLOW       Anywhere (v6)
****/udp (v6)              ALLOW       Anywhere (v6)
21 (v6)                    ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)

I have also tried ```
sudo ufw allow ftp
``` and ```
sudo ufw allow ftp/tcp
```


Clearly I'm making some noob-ass mistake here!

---

### Post by Lars Noodén on 2015-11-12
FTP is difficult.  It's worse if you have to proxy it.  That is one reason on top of the security reasons that it is discouraged.  I suspect you are getting caught by [active FTP and should try passive FTP](http://stackoverflow.com/questions/1699145/what-is-the-difference-between-active-and-passive-ftp).  

Since you can do SFTP from your Android device to your Mac, you should try to your Lubuntu system.  Install the package openssh-server and open port 22 incoming.  Then when you are done, uninstall it if you like.

---

### Post by steve234 on 2015-11-12
so I need to enable ports 2000, 2001 and 1234?

I have an FTP server on my android device - setting up an SSH server on the android device seems to be a world of pain (due to how dropbear works)

---

### Post by Lars Noodén on 2015-11-12
When you connect to the Android device's FTP server, the client ([ftp](http://linux.die.net/man/1/ftp)) might need to use the -p option to tell the server to use passive mode.  Otherwise, the server will need to connect back to the client and that would necessitate turning off the firewall on the netbook as far as I understand.  Again, the standard answer is to use SFTP

Setting up an SSH / SFTP server on your Lubuntu device is as simple as clicking on the package openssh-server in the software center or synaptic, and then opening port 22 incoming with UFW or GUFW.

---

### Post by steve234 on 2015-11-12
the -p option did nothing. 

I may investigate SSH when I have time - but like I said, FTP is more covenient.

---

### Post by Lars Noodén on 2015-11-12
> **steve234 said:**
> the -p option did nothing. 


Ok.  I am out of guesses for FTP.  

> **steve234 said:**
> 
I may investigate SSH when I have time - but like I said, FTP is more covenient.

For me, installing openssh-server on a (L)ubuntu machine takes a few seconds and then it is ready to go:

```

sudo apt-get update
sudo apt-get install openssh-server
sudo ufw limit ssh
sudo ufw enable

```

Or the equivalent in Synaptic or the Software Center.

Then you could use the SFTP client to connect to the Lubuntu machine as you have done connecting to your Mac.

---

