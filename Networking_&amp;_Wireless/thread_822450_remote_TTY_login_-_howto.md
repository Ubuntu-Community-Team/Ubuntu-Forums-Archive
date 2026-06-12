---
title: "remote TTY login - howto?"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by s_raiguel on 2008-06-08
Yesterday evening, while trying out the beta of Google Earth, the entire shell froze, and I could only regain control by rebooting. I remembered that years ago, when I used SuSe Linux and the X-server would hang, I used to be able to log on remotely via TCP/IP, using a simple TTY terminal on a Windows computer - it was as simple as giving the IP number of the crashed computer and the TTY port number (what was this?) of the Linux system. I could then find the number of the offending process and kill it, using the remote terminal. Is it still possible to do this? What has to be running or enabled on the Ubuntu system? Is remote login now only possible with SSH?

---

### Post by s_raiguel on 2008-06-16
Since nobody seemed able, or willing, to provide an answer to this question, I'll provide one myself, one that I came up with after a couple of days' fiddling and looking at various web pages other than those provided here. Turns out the Telnet, or even better, Telnetd service has to be running on the host computer. If that's the case, you can log in using the program "Hyperterminal" provided with Windows XP, on port 23. Here's how you get Telenet running:

sudo apt-get install telnetd

edit inetd.conf using the command 

sudo gedit /etc/inetd.conf

Add this line to the text file and save 

telnet         stream  tcp     nowait  telnetd.telnetd /usr/sbin/tcpd  /usr/sbin/in.telnetd

Run this command to restart the network services, including telnet.

sudo /etc/init.d/openbsd-inetd restart

You can check that the service is running using the command 

netstat -a | grep telnet

you should see a line that looks like this if it's running. If not, it returns nothing. 

tcp        0        0        *:telnet        *:*        LISTEN

Now, get on a Windows box somewhere and start up Hyperterminal. Instead of one of the COM ports, select TCP/IP, then enter the IP number of your Linux box and port 23. You should see your login promt from Ubuntu. Log on, and you're in the system, remotely, and can enter any terminal command. This is an ideal backdoor for regaining control of your system if a malformed program hangs up the X-Windows terminal, freezing out mouse and keyboard input. Simply log on remotely and kill the process that's hanging the system.

---

### Post by Ashinberry on 2009-04-26
(I know this is ancient and I hate to bump but I hate seeing bad advice more)

The reason telnetd isn't installed or configured by default on modern operating systems (linux distributions, commercial UNIX distributions, and Microsoft Windows) is because it completely lacks any form of security. If you must log in remotely then SSH provides all the capabilities of telnet (and dozens more) and has clients available for every operating system. It is typically installed by default but can also be installed with "sudo apt-get install openssh-server".

To address your symptom, rather than your question directly, if X locks up on you then you should use the keyboard shortcut control-shift-backspace, which will kill the X server and restart it at a login prompt. This will also kill any non-responsive program causing lockups without the need to open a lorry sized hole in your system for worms to exploit and without requiring a second computer.

---

