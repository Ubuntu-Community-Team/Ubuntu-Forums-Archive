---
title: "Screen Sharing - No Networks Selected"
date: 2018-12-31
forum: Networking &amp; Wireless
---

### Post by shadowen2 on 2018-12-31
I'll make this quick because I know this is a busy forum.  I'm having trouble enabling screen sharing on my 18.04 LTS system.  I'm using it as a home automation server and it was originally installed as 16.04 LTS and then I decided to update to the newer version this week.  The update went well with the exception of a minor detail.  I'm unable to access the system via VNC.  I've googled around a bit and followed some of the instructions on things to test and I'm just at a loss as to how I can go about diagnosing this problem.  I'll preface this all by saying that everything was working correctly prior to the update.  I have verified that Vino is installed and is the current version along with doing updating via apt.  

What happens is when I go into Settings > Sharing > Screen Sharing if I try to enable it the button will not turn on.  On the bottom of the dialog box I see "No networks selected for sharing."  

I followed the directions here: [https://askubuntu.com/questions/1070520/screen-sharing-no-network-selected-for-sharing-problem-in-unity-control-center](https://askubuntu.com/questions/1070520/screen-sharing-no-network-selected-for-sharing-problem-in-unity-control-center)

but I wasn't able to check my syslog as I'm not sure how I'd do that.  I also looked at the bug report but it appears that I need to upgrade to the latest version of Ubuntu which I'd prefer not to.  I've been using the LTS versions in hopes that something catastrophic like this wouldn't happen where ultimately I'd need to reinstall to repair. 

Thanks!

---

### Post by TheFu on 2019-01-01
I don't use VNC, but here's how to use the log files: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

I use either remote X11 or x2go for graphical programs from a different system.  On the LAN, I use remote X11 through an ssh tunnel because it is so very easy and "just works."

```
$ ssh -X userid@server program
```
If the local and remote userid are the same, then the userid can be left off.

For example, I keep a todo list on my desktop machine in a different room.  It is stored as a LibreOffice spreadsheet.  To run the program on the desktop, but have the GUI display for libreoffice displayed on my laptop here, I use 
```
ssh -X hadar "libreoffice ~/GTD-Todo.ods" &
```
* hadar is the DNS name for the other system.
* sshd_config has to be configured to allow _X11Forwarding yes_. That was the default for a long time. Best to check it.
* for convenience and security, I have ssh-keys setup between the two systems.  The client (my laptop) put my public ssh key on the server, hadar, in the correct place using ssh-copy-id.  More convenient AND more secure.  

The local system must have a running X/Server.  I don't know if Wayland works or not.

---

### Post by shadowen2 on 2019-01-01
Thank you for the response.  Unfortunately using X11 isn't quite what I need in order to function.  I need actual access to the desktop on the remote machine so that I may operate it via the GUI as if I were there.

Very good information on the logs, thank you for that as well.  I did a little fiddling and didn't get anything out of the logs so I'll get to doing some more research but still no joy.

---

