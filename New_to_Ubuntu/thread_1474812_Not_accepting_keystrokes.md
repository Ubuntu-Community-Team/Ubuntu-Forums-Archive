---
title: "Not accepting keystrokes"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by zlot on 2010-05-06
[SIZE=3][COLOR=black]I once tried Kubuntu, and have currently in-place upgraded my existing Ubuntu 9.X to Ubuntu 10.0X, and in both instances, after the install, I am unable to log in to Ubuntu as the console is not accepting my keystrokes.
I was able to go directly to a terminal in Kubuntu and it DID accept keystrokes, but as a newbie, that didn't do me any good.
This problem seems to be in the new versions of Linux, as I have other older, VMs running RedHat, SUSE, Debian, even MAC Leopard, and they are working.
It seems to be with the newer versions that this problem appears.
I AM using a wireless KB(have tied plugging in a wired one) and Virtual Machines(VM Ware 7.1).
Fortunately, I have MS Previous Versions on the host HD and am able to roll back the install to the original version, but would like to address this issue, because it is not going to go away as I have seen it twice now.  
Thanks!
~Z~[/COLOR][/SIZE]

---

### Post by zlot on 2010-05-07
Searching the web, I found the answer on VMWare&#8217;s forum. [User SGiff wrote]("http://communities.vmware.com/message/1515622#1515622"), in part:
 I found the :0-greeter.log file in /var/log/gdm had errors complaining about not find symbols for &#8220;U.S. English&#8221; keyboard layout in us keyboard file. A little grepping later finds &#8220;U.S. English&#8221; is set in /etc/default/console-setup.
<from original file>
XKBMODEL=&#8221;SKIP&#8221;
XKBLAYOUT=&#8221;us&#8221;
XKBVARIANT=&#8221;U.S. English&#8221;
XKBOPTIONS=&#8221;"
 <changed to this, matching other linux installs>
XKBMODEL=&#8221;pc105&#8243;
XKBLAYOUT=&#8221;us&#8221;
XKBVARIANT=&#8221;"
XKBOPTIONS=&#8221;"
 Reboot and keyboard now works at login.
 And indeed it did. To login to the console, left click on the red &#8220;Shutdown&#8221; icon, then select &#8220;Console Login&#8221; from the drop down menu:
 [[IMG]http://reformedmusings.files.wordpress.com/2010/04/lucid_rc_login_options.jpg?w=500&h=376[/IMG]]("http://reformedmusings.files.wordpress.com/2010/04/lucid_rc_login_options.jpg")
 After logging into the console, type at the prompt:
 cd /etc/default
sudo nano console-setup
 Find the offending settings which SGiff pointed out towards the end of the file, make the recommended changes, save the file, then type &#8220;sudo reboot&#8221; at the console prompt. The system restarts. When the GUI login comes up, everything should work fine. It does here.
 Bottom line is that, per VMWare, Workstation 7.0.1 isn&#8217;t yet compatible with Lucid. The elimination of Hal from Lucid probably has something to do with this problem. However, everything else, including VMWare Tools, works just fine.

---

