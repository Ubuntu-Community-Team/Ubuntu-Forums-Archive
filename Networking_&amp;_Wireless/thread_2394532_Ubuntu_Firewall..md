---
title: "Ubuntu Firewall."
date: 2018-06-18
forum: Networking &amp; Wireless
---

### Post by linux-user-0987 on 2018-06-18
Ufw needs to be disabled and enabled every time I restart my computer. The settings are set to block all incoming and outgoing except for the specified ports. 
And when I use the suspend option I need to disable, start firefox, and then enable. Otherwise it won't connect.

I found a page with a similar question but I am looking for a better solution:

[https://stackoverflow.com/questions/41319291/ufw-blocks-most-ports-until-disabled-and-re-enabled-after-reboot](https://stackoverflow.com/questions/41319291/ufw-blocks-most-ports-until-disabled-and-re-enabled-after-reboot)

Operating System:

Is there a linux command which lists all available commands/programs installed in the operating system?

---

### Post by TheFu on 2018-06-18
**sudo find / -type f**
will show all files on the computer. Because a user can place a program **anywhere** on the system that they like and have write permissions to, this is the only method to get a list.  You can tell 'find' to limit the files found to those with execute permissions. I don't  remember exactly how and you can look in the manpages just like I can.  The GUI menus only show the programs the distro creators think worthy of being in a menu. There are many hundreds of other programs and you can install 40K+ more programs from the included repositories easily.  So getting a full list really isn't all that useful.  If you want to learn most pre-installed programs, a _Unix Power User's_ book is probably the most efficient way to learning or there's [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) which introduces commands in a smart order, building on prior information provided.

However, most programs are placed in /bin, /usr/bin, and /usr/local/bin.  Almost all of those programs will have a manpage describing the command, purpose, and all options.

"ufw" is "Uncomplicated Fire Wall" ... which is just an interface into the kernel firewall, which does all the real work.  iptables is another interface to the kernel firewall, as is firewalld.  

There was a bug with ufw that prevented it from automatic startup when configured in the  /etc/ufw/ufw.conf for that.  It has been fixed, so I'd ask first if your system is patched to current levels?  Run  **sudo apt update && sudo apt full-upgrade** to get patched.
Next check that 
```
ENABLED=yes
``` exists and isn't a comment in the /etc/ufw/ufw.conf file.

If these aren't working for your, please clearly show what settings are in the ufw.conf and what you've tried.

BTW, it is best to ask 1 question per thread, because someone expert in 1 area might not be comfortable in all areas of the questions.

---

