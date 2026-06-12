---
title: "Server 10.4 - extremely frustrating"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by rib-rider on 2011-02-28
Hi, I am really new to Ubuntu and not an IT pro as most of the posters seem to be. I installed server 10.10 and through similar problems to the one described below re-installed it four times before installing server 10.4 and getting the same problems. It is really frustrating.

The goal is to use ubuntu server as a media server and to add a second NTFS formatted HDD at a later date but I'm not even able to get to first base at the moment.
Processor is AMD athlone 64, 1.5GB RAM, currently single IDE drive linux dedicated and formatted through guided install. Attached is the screenshot of the installed hardware.

Problem is that both in 10.10 and 10.4 the text entry freezes after about a minute from log in. Most of the commands using apt-get don't seem to work. You can see that I tried to install lshw-gtk and no library was found, this was after seeing a lot of posts about NVIDIA and I was trying to eliminate an issue here but again it failed.

Attempts to use Aptitude freeze before I can download anything. Updates freeze after partial downloads and partial installs as do upgrades. 10.10 updated and upgraded ok but then other commands froze so I thought 10.4 might be better.

Since I'm a bit lost with CLI and thought Ubuntu might be simpler to use if I downloaded the gnome-core but apt-get fails on this too, "not found". I have worked through the Ubuntu documentation and likely fixes don't work because the text editor freezes or the application is not found in the library. 

I feel like the guy crossing the road who has to build the road first. I have checked out the hardware, done a thorough mem test and have not been able to find anything there.

Any advice would be appreciated and am willing to re-install another time before I wrap it up out of frustration.

Regards.....:confused:

---

### Post by drdos2006 on 2011-02-28
Hi
Your server is up and running. lshw-gtk appears to be a graphical interface for 10.4 Desktop, not 10.4 server.
Install Webmin so you can control your server with a Web graphical interface from another machine.
```

Download from your server with,
sudo  wget  http://prdownloads.sourceforge.net/webadmin/webmin_1.530_all.deb

Install with 
sudo  dpkg  -i  webmin_1.530_all.deb

Add extra libraries with 
sudo  apt-get  -f  install

```


Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by rib-rider on 2011-02-28
Hi DR dos,
Thanks I'm sure that would be helpful, I had tried to download webmin previously but it was not found. This time I tried to type in the download command you provided and the text editor just froze, so I was unable to complete it.

If I could stop the thing freezing I'm sure I could make some progress. 

Any ideas? I have re-installed five or six times already and still the same problem.

Regards

---

### Post by drdos2006 on 2011-02-28
This is from a previous thread I saved because it helped me.
My ISP had made some changes to the network and I had constant dropouts until I disconnected IPv6.

> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?
```

From your server, type

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf
From your server, type
sudo  vi  /etc/sysctl.conf
Add the following lines.
# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Write and Save with:  Esc(cape key)  :  w  !	Esc(cape key)  :  q  !

Reboot your server.
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

```
To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

### Post by scorp123 on 2011-02-28
> **rib-rider said:**
> Hi, I am really new to Ubuntu and not an IT pro as most of the posters seem to be. I installed server 10.10  Why don't you install the normal Ubuntu Desktop if you need a GUI? The differences between the "server" and the "desktop" version is that there is no desktop GUI in the "server" version and that the kernel used in the "server" version has a few options activated that the desktop version hasn't (and those options are not really interesting to 99% of the general population out there), but other than that they are still the same OS with the same packages. Means: You can turn the "Server" into a desktop installation by installing desktop GUI packages, or you can turn the "Desktop" into a server by installing the server packages you want.

If I were you I'd install the desktop OS (and remember to activate remote desktop access!) and then install the server packages you need. It would be way easier for you to use this way while you still are a beginner.

---

### Post by TechWiz2100 on 2011-02-28
I only recommend server if you are extremely comfortable with the CLI but if you are comfy cozy with terminal, use it! GUIs on servers are said to be serious security risks (I dun really know about that but w.e)

Otherwise scorp's got the right idea since desktop can run the services of server and you can always kill gnome so its just CLI after your services are configured and running.

---

### Post by rib-rider on 2011-03-01
Thanks to all for some very useful tips. I did think about the desktop way to go but was dissuaded from doing that by security concerns I read about. I'll shoot for one more try with the server and webmin but using 10.10, following drdos approach. If that seriously bombs then it'll be desktop for me.

Thanks for your help and support. Whichever way I go it sounds like it's going to take a bit of time.

Cheers
rib-rider

---

### Post by drdos2006 on 2011-03-01
I had quite a few problems installing 10.10 ( both 64 and 32 bit ) on my ASUS motherboard with DDR2 RAM. I finally got 10.4 LTS 64 bit to install correctly. 

regards

---

### Post by scorp123 on 2011-03-02
> **rib-rider said:**
>  but was dissuaded from doing that by security concerns I read about.

The GUI alone is no security risk per se. What matters is what services you are offering to the outside world (e.g. SSH?? Telnet? FTP? Web?) and how you are securing those (e.g. firewall rules). Also you have to be aware that certain services such as FTP and Telnet are *NOT* encrypted whatsoever and that using them is a great risk (hence why it is better to use SSH, SCP and SFTP as those use strong encryption).

If nothing is activated then nothing can be hacked, because a hacker has no service he could connect to. It's that simple. If you are using server programs and offering network services such as SSH or web services then you might be vulnerable. I'd therefore recommend you read about securing those services, restricting access, and so on.

And make sure you use safe passwords. Using e.g. *"password"* as password is a seriously bad choice. Using *"Pä$Sw0rD!"* is better, but it's still based on a dictionary word. Programs such as **pwgen** (needs to be installed separately) will generate truly and next-to-impossible-to-crack passwords for you, e.g. **O!Hwh2G&4B!* ... and with a little bit of exercise you can even easily memorize such passwords.

The above example could be easily memorized by linking it with a story. 

**[COLOR="Red"]*O!H[/COLOR]**  (like "Oh!" except the order of letters is messed up)
**[COLOR="Red"]w[/COLOR]**e
**[COLOR="Red"]h[/COLOR]**ave
**[COLOR="Red"]2 G[/COLOR]**irls
[B][COLOR="Red"]&
4 B[/COLOR][/B]oys[COLOR="Red"]**!**[/COLOR]

There you go. You just memorized a complicated password such as **O!Hwh2G&4B!*

Of course, it would be unwise to use this very example here :D


Keep your PC patched, and know what you are doing and *why* you think you need to do it. If you do that than having a GUI or not shouldn't really be a big security problem. There are far greater security risks such as badly chosen passwords, incorrectly configured firewalls, etc.

---

### Post by The Cog on 2011-03-02
It's easy enough to disable the GUI if you want to later.

Maybe you need to update your repository index before you can download any other packages. Try the command
**sudo apt-get update**
and see what that says.

---

