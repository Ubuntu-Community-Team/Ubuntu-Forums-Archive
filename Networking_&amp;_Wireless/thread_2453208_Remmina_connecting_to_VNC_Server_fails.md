---
title: "Remmina connecting to VNC Server fails"
date: 2020-11-05
forum: Networking &amp; Wireless
---

### Post by johnaaronrose on 2020-11-05
I'm running Ubuntu 20.04 (fresh install from 20.04.1 & software up to date) on my new main fast computer. I want to desktop share my old NUC Barebones computer, running Xubuntu 20.04 (fresh install from 20.04.1 and software up to date] which I want to use for limited activities such as ip camera usage (using motion app) and VPN away from home. I don't really care much which VNC Client & Server apps I use. So I'm trying Remmina on my Ubuntu 20.04 main fast computer and VNC Server Connect on my old NUC Barebones computer. However, connection fails from the VNC Client to the VNC Server. I've tried in Remmina both RDP & Remmina VNC Plugin. 
PS I'm happy to use other VNC apps if they will work.

---

### Post by TheFu on 2020-11-05
VNC and RDP shouldn't be used.

Use tools based on the NX protocol which leverages the ssh authentication and tunneling methods. These are more secure and faster, almost always.  x2go works very well or you can use Spice through an ssh tunnel or VPN.  x2go feels 2-3x faster than rdp or vnc alternatives on Linux.
[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04) has step by step instructions.

Spice works to access clients running inside a KVM virtual machine under libvirt. It is FAST - freakin' fast!  But doesn't work without libvirt or more accurately, I haven't gotten it working except for remote virtual machines.

The only tricks to x2go is to have ssh already working between the systems and to avoid Gnome3 as the desktop used. Gnome3 really wants direct access to the GPU which isn't possible over a remote connection.

---

### Post by johnaaronrose on 2020-11-06
@TheFu Thanks for the advice.
I've installed x2go's client & started it OK on my Ubuntu box. I've installed x2go's server (no questions asked during install) on my Xubuntu box but there doesn't appear to be a menu entry to start it. How do I start it?
I'm running GUFW on both boxes with SSH configured rule set (i.e. port 22 TCP protocol allowed in) and all outgoing ports allowed. Are there any other ports needed to be allowed in?
I still have Real VNC Connect Server menu entry active even though I've uninstalled it: when I run it, it immediately asks for my password. Am I correct in stating that that is not x2go server?

---

### Post by TheFu on 2020-11-06
x2go-server runs automatically like any other service/daemon does.  It will be started at reboot automatically too.  But ssh-server must be working.  

Hopefully, you've secured the ssh-server and setup ssh-keys for authentication. This isn't strictly required, but I've posted steps in these forums multiple times.  x2go only uses the same ssh TCP port, no others are needed for inbound connections. If you want audio and file sharing between the client and the server, then you'll need to setup bi-directional ssh. This is easy on the same LAN without any firewalls, but nearly impossible over the internet, since we usually can't have a port forwarded to our desktops from a remote hotel or even most businesses.

Real VNC is completely separate. I'd stop that service. You'll see.

With the x2go client, be certain you choose the settings you want.  For the connection speeds, I usually use 1 less than the truth. The less bandwidth, the less traffic, and the faster everything performs.  Another key setting is to DE you connect into. You can't just choose one randomly. The DE must be installed on the remote system.  XFCE is a good compromise, but you can use almost any of them except Gnome3 or Unity.  I use a custom setting into fvwm, but I wouldn't recommend that for anyone else who isn't addicted to fvwm already.

---

### Post by johnaaronrose on 2020-11-06
Still not fully with it.
 I've installed openssh-server package on my Xubuntu box. I've done the required sysctl commands e.g. sudo systemctl start ssh.service, sudo systemctl status ssh.service, sudo systemctl enable ssh.service, sudo systemctl is-enabled and ssh-server is looking good. 
Re secured the ssh-server and setup ssh-keys for authentication: can you point me to a post on that?
Re audio & file sharing between the client & the server, you say that I'll need to setup setup bi-directional ssh. How is that done between openssh-server & (client) ssh?
However, even though I've installed x2goserver and its dependencies (e.g. those starting with x2go-server), I'm not able to start the service with sudo systemctl x2go.service start or sudo systemctl x2goserver.service: it comes up with service not found for both commands. What is the correct command?
BTW I've got rid of all RealVNC bits: even though I purged it, it still left some directories & files. I found webpage on RealVNC's website ([https://help.realvnc.com/hc/en-us/articles/360002250957-Completely-Removing-VNC-Connect](https://help.realvnc.com/hc/en-us/articles/360002250957-Completely-Removing-VNC-Connect)) giving details of them. I tend to get put off using apps which are difficult to remove, as they are often low quality.
When you talk about the remote system, do you mean the one with the x2go client or the one with the x2go server? if it's the server, the I don't need to do anything as that's an Xubuntu instal, which uses xfce.

---

### Post by TheFu on 2020-11-06
I can't remember the last times I had to start x2go or ssh on any of my systems.  The installer does that on Ubuntu, IME.  I don't use systemctl commands, sorry. I'm old school still, but again, I haven't needed to manually start either x2go or ssh on my systems in years.

Typically a "server" is remote.

If **ssh userid@remote-server** works, then that is all that is needed for x2go to work too. If the userid on the client and the server are the same name, then you can leave that off. If ssh from the client to the server doesn't work, then x2go will not work. Stop and get that working before doing anything else.  Setting up ssh isn't hard or very many commands. If you think you need over 5 total, then I think you are making it harder than it needs to be.  I'm assuming default ubuntu installs. If you aren't using default ubuntu - --- like some VPS version, I can't help. They don't leave the defaults. Find help on the VPS documentation.  And never, ever, use root for remote ssh or x2go. That cannot be used.

For fun, I ran this:
```
$ systemctl status x2goserver.service 
&#9679; x2goserver.service - X2Go Server Daemon
     Loaded: loaded (/lib/systemd/system/x2goserver.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2020-10-31 04:08:27 EDT; 6 days ago
       Docs: man:x2goserver.conf(5)
   Main PID: 1010 (x2gocleansessio)
      Tasks: 1 (limit: 4617)
     Memory: 311.1M
     CGroup: /system.slice/x2goserver.service
             &#9492;&#9472;1010 /usr/bin/perl /usr/sbin/x2gocleansessions

Oct 31 04:08:25 regulus systemd[1]: Starting X2Go Server Daemon...
Oct 31 04:08:27 regulus systemd[1]: Started X2Go Server Daemon.
```

regulus is a 20.04 Ubuntu-Mate desktop, but I connect via x2go using fvwm in the "Session type" under a custom command.

Forget about local shares and printing for now. If you can't walk, why try to sprint?

You seem to be missing some basic Linux knowledge.  To fill in the gaps, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
Running commands with incorrect options will not gain correct results.

---

### Post by johnaaronrose on 2020-11-07
I'm able to do 'ssh john@192.168.101.12' from my Ubuntu box (i.e. to my Xubuntu NUC box running the ssh server) with openssh-server installed, enter the requested password, and then do Terminal commands (such as ls) as though I were physically typing on that box.
I purged x2goserver and its dependent packages from my Xubuntu box and installed x2go-server and its dependent packages on that box. I checked that x2go server was running on that box: 
john@JohnNUC:~$ systemctl status x2goserver.service
&#9679; x2goserver.service - X2Go Server Daemon
     Loaded: loaded (/lib/systemd/system/x2goserver.service; enabled; vendor pr>
     Active: active (running) since Sat 2020-11-07 16:35:41 GMT; 15min ago
       Docs: man:x2goserver.conf(5)
   Main PID: 2317 (x2gocleansessio)
      Tasks: 1 (limit: 9397)
     Memory: 16.8M
     CGroup: /system.slice/x2goserver.service
             &#9492;&#9472;2317 /usr/bin/perl /usr/sbin/x2gocleansessions


Nov 07 16:35:40 JohnNUC systemd[1]: Starting X2Go Server Daemon...
Nov 07 16:35:41 JohnNUC systemd[1]: Started X2Go Server Daemon.

When I started x2go client on my Ubuntu box, it started OK. It came up with the session preferences window. i completed the preferences information as specified in [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04) i.e 192.168.101.12 for Host, john for Login, XFCE for Session Type. Looking at "Finally, because you connect to the server with SSH keys, click the folder icon next to Use RSA/DSA key for ssh connection and browse to your private key. If you didn’t opt to use the more secure SSH keys, leave this empty; the X2Go client will ask for a password each time you log in.", I left "RSA/DSA key for ssh connection" blank. I expected to be asked for a password when I clicked "the white box that includes your session’s name on the box’s top-right side": screenshot of that window is attached. But I wasn't asked for a password and nothing happened. I don't see any log file for x2go on either box. Any ideas on what I should look at now?

---

### Post by TheFu on 2020-11-07
Double click on JohnNUC to connect?

This isn't supposed to be hard. It "just works" for everyone.

If you use ssh-keys, only the ssh-key unlock password, if you made one, will be requested, if the ssh-agent timeout has expired. If not, then you won't be prompted and a window of the resolution in the settings will open.  Generally, don't touch the ssh stuff unless the client is MS-Windows. For Unix-to-Unix, the ssh settings outside x2go just work.

Just try different things, but really, everything should just work with the defaults. Always has for 100+ people I've helped. The only tuning I ever do is changing the image compression and lowering the bandwidth, usually to ISDN. These have nothing to do with the authentication part.

Have you found the x2go project website?  Shouldn't need it just to get a connection working, but there are tips and FAQs there. I'm assuming the issue is something so basic that my experience is a problem. Things 2nd nature to me.  Defaults for everything work, except picking the session type.

ah .. if you didn't setup ssh-keys, then leave all ssh settings empty inside x2go. See how that works.  I always use keys for authentication - always.  Passwords are a security liability.

---

### Post by johnaaronrose on 2020-11-08
> **johnaaronrose said:**
> I'm able to do 'ssh john@192.168.101.12' from my Ubuntu box (i.e. to my Xubuntu NUC box running the ssh server) with openssh-server installed, enter the requested password, and then do Terminal commands (such as ls) as though I were physically typing on that box.
I purged x2goserver and its dependent packages from my Xubuntu box and installed x2go-server and its dependent packages on that box. I checked that x2go server was running on that box: 
john@JohnNUC:~$ systemctl status x2goserver.service
&#9679; x2goserver.service - X2Go Server Daemon
     Loaded: loaded (/lib/systemd/system/x2goserver.service; enabled; vendor pr>
     Active: active (running) since Sat 2020-11-07 16:35:41 GMT; 15min ago
       Docs: man:x2goserver.conf(5)
   Main PID: 2317 (x2gocleansessio)
      Tasks: 1 (limit: 9397)
     Memory: 16.8M
     CGroup: /system.slice/x2goserver.service
             &#9492;&#9472;2317 /usr/bin/perl /usr/sbin/x2gocleansessions


Nov 07 16:35:40 JohnNUC systemd[1]: Starting X2Go Server Daemon...
Nov 07 16:35:41 JohnNUC systemd[1]: Started X2Go Server Daemon.

When I started x2go client on my Ubuntu box, it started OK. It came up with the session preferences window. i completed the preferences information as specified in [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04) i.e 192.168.101.12 for Host, john for Login, XFCE for Session Type. Looking at "Finally, because you connect to the server with SSH keys, click the folder icon next to Use RSA/DSA key for ssh connection and browse to your private key. If you didn’t opt to use the more secure SSH keys, leave this empty; the X2Go client will ask for a password each time you log in.", I left "RSA/DSA key for ssh connection" blank. I expected to be asked for a password when I clicked "the white box that includes your session’s name on the box’s top-right side": screenshot of that window is attached. But I wasn't asked for a password and nothing happened. I don't see any log file for x2go on either box. Any ideas on what I should look at now?

I figured it out. Looking at the wX2Go wiki [https://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](https://wiki.x2go.org/doku.php/wiki:repositories:ubuntu), I also had to install x2goserver-desktopsharing using apt. Also, I had to run the X2Go Desktop Sharing app on the server (i.e. my Xubuntubox). I forget whhich of installation or running X2Go Desktop Sharing asked gave me checkbox options in a popup: I marked each option. 

The wiki said when running X2Go Client (on my Ubuntu box):
Preparing the session:
Create a new session with “session | new session…”.
Assign a session name.
As 'host name' give the name of the machine, the session you want to connect to, is running on.
As 'user name' give your account on the remote machine.
As 'session type' choose 'connection to local desktop'.
Recommended: choose “full screen” on the settings tab. Otherwise, everything can become too small to read.
Press 'OK' to save the session.

I named the new session JohnNUC (i.e. Xubuntu box's hostname) with 'Host Name' as my Xubuntu (i.e. X2Go Server) NAT ip address, username my Xubuntu box's login name (to save confusion I have john as the login name for both boxes), Session Type as X2Go/X11Desktop Sharing. On the Connection tab, I set Speed to LAN as I don't intend to use X2Go away from home, though I might change my mind on that and I then would setup a new session for that. On the Input/Output tab, I selected Custom & then 1366x768 (which is the screen size that my Xubuntu box uses on its small monitor as opposed to the default 800x600 and which is smaller than the screen size of 1920x1080 for the monitor on my new desktop box) and kept the default Bidirectional Copy & Paste option. On the Media tab, I kept the default 'Enable sound support' and selected the 'Client side printing' option.. On the 'Show folders' tab, I browsed to my home folder of john, clicked Add and selected the Automount option.

Overall, X2Go's documentation is slightly out of date for Ubuntu (and therefore Xubuntu 20.04) but using it is a good experience. I used to use RealVNC cConnect Client & Server before I built my new Ubuntu 20.04 box & replaced my Raspberry PI with my old NUC box with a fresh install of Xubuntu 20.04. If anybody wants a Raspberry Pi model 3 (including Raspbian Buster install on an SD Card) gratis, please let me know.

---

### Post by TheFu on 2020-11-08
> **johnaaronrose said:**
> ...  install x2goserver-desktopsharing using apt. 


I've never, ever, needed to install that. Not once. Never.  Not on any Ubuntu release.  OTOH, I've always used the x2go PPA, not the ubuntu repos. [https://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](https://wiki.x2go.org/doku.php/wiki:repositories:ubuntu) I figured the repo versions would be fine and didn't want to confuse farther.  The PPA is managed by the x2go team, so it is always current.

Update: Looked up what x2goserver-desktopsharing was.  I've never wanted the actual desktop. Always wanted a virtual desktop, since most of my uses are with virtual machines on headless servers. I suppose people used to Windows or VNC might expect that. I have only 1 screen for about 15 systems. You can use 1,5,20,150 and more virtual screens/sessions without needing any gpu at all. It is a different way of thinking, I suppose.

Regardless, happy you got it working.  Be certain to secure your ssh connection if you make this work over the internet and never use passwords to connect over the internet.  Use ssh-keys.  ssh-key are one of the few "better security" things that are both more secure (significantly) AND more convenient (so, so, so, so, much more convenient).  ssh-keys "just work" on all Unix systems, once setup.  Securing ssh about 90% is usually just **sudo apt install fail2ban**. The defaults are sufficient and it starts and integrates into Ubuntu from that point on.  If you want more ssh security, google "securing ssh".
Here's mine: [https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) , but there are lots of others.

Anyways, happy you got it working.  You can speed up the connect with just a few tweaks to the compression used without visually impacting the display where you'd care/notice.

If this is solved, please mark it that way using the Thread Tools button near the top of the page. That helps the community - both people looking for solutions and people looking to help.

---

### Post by TheFu on 2020-11-08
You can re-purpose that r-pi to be a pi-hole. That will drastically speed up your internet use by doing some ad blocking.  Having 1 r-pi around for little stuff is handy, even if you don't need it today.  For example, as a music server or remote music player in a different room of the house or ... a r-pi v3 is great as a Kodi system for video playback that isn't 4K.  

If you haven't played with nextcloud, there are easy instructions to run that on a Pi and a pi-3 is more than capable of serving a typical home with files, calendars, contacts, and perhaps even video chat. I have nextcloud running in a VM on a pentium dual-core system. It handles 7 video streams for family conferences every month through nextcloud-talk.  About the only things I wouldn't put on a r-pi would be WAN router/firewall or VPN end-points, but everything else, sure. Why not?

---

### Post by johnaaronrose on 2020-11-08
I've marked this thread as solved. Should I start new thread(s) for my questions below?

I've taken a look at the downloaded pdf version of the Linux command book at that you recommended and have ordered the print version: it looks good for the Unix command stuff (a lot of which I already know due to past work experience except for such things as vi) but it doesn't get to grips with the networking & security stuff such as ssh which I have very limited knowledge of. Have you got a book recommendation for that stuff? 

Bidirectional Copy & paste is not working between my X2Go Client & X2Server boxes. Can you think of any reason why?

I've noticed that if my X2Go server box 'suspends' (due to my Screensaver Preferences of Blank screen which then requires inputting of its Xubuntu login password to get it going again), that the X2Go client on my Ubuntu box makes it difficult to input that password. I hoped that the restore option of the X2Go client on the System Tray would do that but it didn't. Any ideas?

If I used the Pi as a pihole does that mean that I would have to connect it to my router and have my Ubuntu box (and my Xubuntu box running ssh server & X2Go server connect to it? Otherwise, how would ads be blocked to my Ubuntu box (i.e. if the PI & Ubuntu boxes were both directly connected to my router)?

I took a look at [https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) The 'egrep -i Failed /var/log/auth.log*' command (run on the ssh server & x2go server box) only displayed 3 fails. I'm just wondering if there are so few because my NAT subnet is 192.,68.101 rather than the usual suspects of 192.168.0 and 192.168.1: I forget where I saw that recommended change and why it was recommended. Am I correct?

On your above website (of [https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) looking at the 'Listen on a Non-standard Port' section, I don't understand why the first method of 'Use Port Translation on the Router' will stop hackers from trying port 22. Is it because there is no Port Forwarding on the router from port 22 to port 22? In the 'change the port on your gateway ssh server', I presume that this would be the (JohnNUC) box running both the ssh server & the X2Go server? I guess that I'm again showing my ignorance of Networking & Security. Are there any reasons to prefer one method to the other?

Do you recommend installing fail2ban on both my Ubuntu box & my Xubuntu box?PS with all my fiddling about, I now have openssh-server installed on my Ubuntu (i.e. X2Go client) box, my main box.  Can you think of any reason why I should need it installed on that box. Only reason I can think of is to be able to access the box remotely: in which case I should probably install X2Go server on it.

---

### Post by TheFu on 2020-11-08
Cannot recommend any specific books, but O'Reilly  have all the Unix books for decades. There is a book for each network service. It s overwhelming at first. Like eating an elephant.  Just take 1 bite at a time.

A pi-hole is just a DNS for your that can filter using regex.
RegEx is "regular expressions". It is a language for matching patterns. Simple regex is what grep uses. Full regex s what perl, ruby, python and other "enhanced regex" engines use.

There is a book on ssh.  ssh s the backbone for how unix systems communicate, transfer files, support remote logins, remote sessions, remote X11, do backups, support remote file systems over the internet, etc.  I've never read that book.

Fail2ban is just an easy way to monitor logs and take actions based on log entries. That's the general answer. It is pre-setup to look for brute force ssh attempts and create a firewall rule to block failures for some time period.  I run an sh-server on all my sytems, so I have fail2ban installed too.

x2go should be the exception for connections.  Use plain ssh 99% of the time.  On the LAN, there is no real reason to use x2go. Just use remote X11 to run gui programs on other systems.  Plus select/paste is built-into X11.

---

