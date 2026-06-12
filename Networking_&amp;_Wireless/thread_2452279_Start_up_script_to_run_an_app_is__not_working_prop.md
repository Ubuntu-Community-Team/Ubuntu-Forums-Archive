---
title: "Start up script to run an app is  not working properly"
date: 2020-10-19
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2020-10-19
Can you please tell me what is wrong with this approach in 20.04:
a. When starting up an error message comes:
    Authentication required to run 'usr/bin/env' as SU 
     As I have changed sudoers I do not expect authentication to be required. 
b. As part of the boot process there is an error message: Access control disabled. Access denied. I have not been able to find the error message 
    in the boot log or dmesg.

 ---------------------------------------------------------------------------------------
This is how I set up the auto run script on start up

1. create a startup action In startup apps: 

Name: vpn.com startup

command:
	gnome-terminal --command="/usr/local/vpn.com/bin/run_debian.sh"

2a. Change name of run_debian to run_debian.sh

2. Edit   /etc/sudoers as Super user::
	a. Add into sudoers by typing:
		1. robin ALL=(root) NOPASSWD: /usr/local/vpn.com/bin/run_debian.sh
       b. save file
		


3. Set  run_debian.sh to  be  owned by root:root
	sudo chown -c  root:root   /usr/local/vpn.ac/bin/run_debian.sh
	
The above should run the setup including the script provided by the vpn, without the need for authentication. 

I am finding the vpn is not being run at startup. I have to run it manually as program. I wanted it to be automatic.

---

### Post by TheFu on 2020-10-20
usr/bin/env
is probably the wrong path.
**[COLOR="#FF0000"]/[/COLOR]usr/bin/env** is what you need.

Always use **sudo visudo** to modify the sudoers. It checks for problems in the changes.

What are the permissions on  /usr/local/vpn[COLOR="#FF0000"].ac[/COLOR]/bin/run_debian.sh?
What are the permissions on /usr/local/vpn[COLOR="#FF0000"].com/[/COLOR]bin/run_debian.sh?
Did you mean for those to be different?

What do you mean by "startup action?"  Is that at boot or after a GUI session login finishes?

---

### Post by Robbyx on 2020-10-20
> **TheFu said:**
> usr/bin/env
is probably the wrong path.
**[COLOR="#FF0000"]/[/COLOR]usr/bin/env** is what you need.

Where should I look for the set up of that path? 

> 
Always use **sudo visudo** to modify the sudoers. It checks for problems in the changes.

What are the permissions on  /usr/local/vpn[COLOR="#FF0000"].ac[/COLOR]/bin/run_debian.sh?
What are the permissions on /usr/local/vpn[COLOR="#FF0000"].com/[/COLOR]bin/run_debian.sh?
Did you mean for those to be different?
No.
Please assume the first one is .com  and they point to the same run_debian.sh
It is root/root

> 
What do you mean by "startup action?"  Is that at boot or after a GUI session login finishes?

The entry is in the startup applications. I assume that means it should run at boot.

---

### Post by TheFu on 2020-10-20
root/root are not permissions. That is just the owner and group.  What are the permissions?  **ls -al** shows it. Any script must have execute permissions to be run, depend on the language used, and the effective userid running the process, there might be other permissions needed.

Extensions like .sh are helpful for humans, but the system doesn't care at all.  Extensions aren't used on Unix systems by the OS.

As described, 'Startup applications' are not at boot. They are at login, once a GUI session is created through a login.  If you need something to begin at bootup - probably after networking has been started, then system files much be modified and the script needs to be 100% safe to run without any GUI.

I cannot answer the first question. It would depend on where that mistake was entered.

---

### Post by Robbyx on 2020-10-25
I have it working by putting sudo in front of the startup command in software startup. However there are error messages coming up in what looks like the terminal, at the time the program is run by software startup. I am wondering what they are but they flash past too quickly for me to read.  I can see them on the screen but not in a log. How can I divert the screen output to a file?



PS
I found the solution of putting sudo in front of the startup software command from a query at 

[https://askubuntu.com/questions/167847/how-to-run-bash-script-as-root-with-no-password#167885](https://askubuntu.com/questions/167847/how-to-run-bash-script-as-root-with-no-password#167885)

---

### Post by TheFu on 2020-10-25
I would rather see just the command needed inside the script that actually starts the VPN get the sudoers NOPASSWD setting, not the entire script, but because you've placed the script in a system directory, not in a user's HOME somewhere, it really shouldn't matter too much. 

Happy you found a solution ... or a better understanding of how sudo works.

Please mark this thread as SOLVED using the Thread Tools button near the top of the page to help others out who are trying to accomplish the same result.

---

### Post by Robbyx on 2020-10-25
Thank you for you help and support. Before  I close the query could you please address my comment in #5?

>  there are error messages coming up in what looks like the terminal, at the time the program is run by software startup. I am wondering what they are but they flash past too quickly for me to read. I can see them on the screen but not in a log. How can I divert the screen output to a file?

or, how do I slow the passing of the error messages, or  where do I look for a log with the same messages?

---

### Post by TheFu on 2020-10-25
I'm not a GUI user, so I can't answer that.  GUI programs often spew junk output that isn't actually errors to stderr. They expect most people will be pushing a button to start their programs, so all stderr and stdout is sent to /dev/null, i.e. nowhere. /dev/null is a device on all Unix systems that is used to eat junk and do nothing with it.

But [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) contains many helpful bash techniques, including how to do stdout and stderr redirection.

All sudo commands are logged, unless you turned that off. Those logs are in /var/log/ somewhere. grep can find them easily.
```
$ egrep sudo /var/log/*g
```
grep/egrep is a very powerful tool.  There is probably some GUI log viewer too. I've never used one of those.

Regular commands don't get logged anywhere, unless the program is setup to use a logging facility or to redirect to a log file.  You can set that up using the link above, if desired.

---

