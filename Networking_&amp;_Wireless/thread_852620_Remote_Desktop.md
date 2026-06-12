---
title: "Remote Desktop"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by reviver on 2008-07-07
I'm new to the Ubuntu forums and I apologize if this has already been covered quite a bit.  I searched around the forums quite a bit and hit some bits and pieces of solutions, but my problem still isn't solved.

I'm trying to run an Ubuntu box as what you guys might call a "headless server", but I'm not running it specifically as a server edition of Ubuntu or anything.  In fact, I'm running Ubuntu Desktop 8.04 LTS (x86 if it matters).

What I mean by "headless server" is simply that I'd like to use the box by some type of remote access so I only need to give the box power and a network cable (and I'll only be accessing it on my local network... no need for SSH tunneling, etc.).

So, I started to set it up by using the native Remote Desktop in Ubuntu to do this.  In the preferences, under the General tab, I checked allow other users to view and allow other users to control.  Then, I made sure ask for confirmation was unchecked and checked the require password and entered it.  Then, under the Advanced tab, I unchecked only allow local connections as well as use an alternate port and require encryption.  I do have lock the screen on disconnect checked, but that has nothing to do with my problem.

To test to see if Remote Desktop was even working at this point, I connected to the Ubuntu box from itself.  Success.  Then, I really wanted to test it so I restarted the machine and went to another computer to try to connect to it.  The connection was refused.  In my Windows-thinking mind, I figured that I needed to enable some type of Remote Desktop service to allow the connection if the computer is at the login screen, rather than already being logged in.  I checked the services and there were no Remote Desktop services, so I came to these forums and searched.  I eventually found out that I needed to go to System -> Preferences -> Login Window and change the Login Style under the Remote tab to something other than disabled.  I set it to Same as Local.  I figured that this solved my problem of not being able to login remotely, so I restarted the box and went off to my other computer to try again.  Still, connection refused.  At this point, even though I knew I was on the right track, I figured I could have missed something at the Login Window settings, so I went back there and started looking around.  On the Security tab, I thought I found the problem solver when I saw that Deny TCP Connections to Xserver was checked.  So I unchecked it, rebooted the machine and went back to the other computer to try again.  Still, connection refused.  And that's where it sits right now because I'm not sure what to try next.

Also, I was trying both the hostname and the IP address when trying to connect all along the way.

Any ideas on what I should try next?

Thanks for the help and sorry for the long length of the post.  I figured it'd be better to be overly descriptive and simple than to overlook things.

---

### Post by mkokotovich on 2008-07-07
What happens when you log in locally to the server, then go to the other machine and try to remote desktop in?

You don't have a firewall running on the server, do you?

---

### Post by reviver on 2008-07-07
If I log into the box locally and then go to another computer to try to connect remotely, I am able to connect to it.

I don't believe I have a firewall running unless there is one that is installed automatically in Ubuntu 8.04.  I haven't installed one either for that matter.

---

### Post by mkokotovich on 2008-07-07
So it seems like you need to have a gnome session running in order to log in... 

Double check that the remote desktop process is (or more likely, isn't) running when you are not logged in.  So logout, then press CTRL-ALT-F1.  This will bring up a terminal, which you should log into, then run: ps aux | grep <insert name of service here>

When you are logged into gnome, this should be running. When you aren't, it seems like it won't be.  I don't actually know what the name of the process will be, I've never used the remote desktop, I always just use ssh.

---

