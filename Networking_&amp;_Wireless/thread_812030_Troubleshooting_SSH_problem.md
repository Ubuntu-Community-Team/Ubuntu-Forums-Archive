---
title: "Troubleshooting SSH problem"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by crashtest on 2008-05-29
I'm running Ubuntu 8.04 on a new Lenovo T61 Thinkpad.  I have a problem using SSH to connect to the Linux network at my office.  The connection can be established, but then freezes after a few moments.  I've been trying to troubleshoot this issue for a while with no luck, but I have learned a few things which may shed some light on the issue:

1.  I've had this problem with many Linux distro's, running on various notebooks or desktop systems at home.
2.  I have no problem if I run PCLinuxOS on the same hardware - in fact this may be the only Distro I've used that does NOT have this problem.  (Note:  I don't want to use PCLinuxOS - I want to run Ubuntu)
3.  Lengthy Google searches always lead back to the same suggestion: change the MTU setting for the network adapter.  I've tried this with many different MTU sizes, and it makes no difference
4.  I compared the default MTU settings on both Ubuntu and PCLinuxOS and they are the same: 1500.  I think MTU can be ruled out.
5.  Makes no difference if I run with wireless or wired connection.
6.  There are slight differences in the version of OpenSSH on Ubuntu 8.04 and PCLinuxOS 2007: PCLinuxOS has OpenSSH 4.5p1, Ubuntu 8.04 has OpenSSH 4.7p1
7.  I tried using putty to make the SSH connection - this didn't help - same problem
8.  Running on PCLinuxOS, I start the SSH connection using Konsole which is a KDE application.  Hmmmm... could this be the issue???  Installed Konsole on Ubuntu - no difference.
9.  Both distros have IPV6 enabled

Again, to summarize - two different Linux distros running on the same hardware, behind the same router, connecting to the same external network, and using the same MTU settings.  One works, the other does not.

(By the way, I've had the same problem with Fedora, Suse, Slackware, Arch, etc etc.  The only one the works for me is PCLinuxOS - AND I DON"T WANT TO RUN THAT.  I'm not a big KDE fan...)

What am I missing here?  What to check next?  Thanks in advance for any help!

---

### Post by elamericano on 2008-05-29
There are some configuration options you could try in ~/.ssh/config.

see: man ssh_config

I'd recommend starting with:
AddressFamily    inet

you also might try a different cipher:
Ciphers    3des-cbc

Do you have access to the ssh server? That's the place to turn on debugging. I had an Apple machine where I could start a second instance of sshd on a different port in debug mode, and I could see exactly what was happening when I connected with Ubuntu.

---

### Post by kevdog on 2008-05-29
This is really a tough problem.  I would definitely stop using an ssh GUI client and head to the command line.  I would definitely connect with ssh -vvv (3'v's) to provide verbose output, and then let the machine sit to see if any error messages popup when the process freezes.

What exactly freezes, the internet connection or ssh? (Need to separate which is the culprit).  When the ssh connection freezes, can you do a ping or use firefox or some other process to connect to the internet?  What does dmesg show?

Again way too many things could be causing the problem.  Lets narrow the possibilities.  Get rid of IPv6 if you don't need it also.

---

### Post by crashtest on 2008-05-29
Thanks - interesting ideas.  I found the ssh_config file in /etc/ssh - there was nothing in ~/.ssh except for the known_hosts file.  I thought I would try replacing the Ubuntu ssh_config file with the PCLinuxOS file to see it that made any difference.  Both files are mostly commented lines, with the only differences noted below:

Ubuntu:
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

PCLinuxOS:
    ForwardX11 yes
    ForwardX11Trusted yes
    Protocol 2,1
    StrictHostKeyChecking no

So I tried using the ssh_config file from PCLinuxOS, but it didn't help.  I also tried your suggestion regarding AddressFamily inet, but again this changed nothing.  (Both the original ssh_config files had the AddressFamily line commented out.)

I do have access to the ssh server, so tomorrow I'll try your suggestion about running another instance of sshd with verbose logging enabled.  I'll also try bringing the Ubuntu notebook in to the office as I'm curious to see what happens when I ssh from the same subnet.

Thanks again for your suggestions.

---

### Post by crashtest on 2008-05-29
> **kevdog said:**
> This is really a tough problem.  I would definitely stop using an ssh GUI client and head to the command line.  I would definitely connect with ssh -vvv (3'v's) to provide verbose output, and then let the machine sit to see if any error messages popup when the process freezes.

What exactly freezes, the internet connection or ssh? (Need to separate which is the culprit).  When the ssh connection freezes, can you do a ping or use firefox or some other process to connect to the internet?  What does dmesg show?

Again way too many things could be causing the problem.  Lets narrow the possibilities.  Get rid of IPv6 if you don't need it also.

I normally do run from command line.  Using putty (GUI client) was an experiment to see if anything changed.  What I do is open an xterm (or Gnome Terminal or Konsole - makes no difference which) and type ssh <hostname>.  I get the username & password prompts and login successfully.  From there if I do something like 'ls -la' I'll get several lines of output and then the terminal freezes.  That's it.  Nothing brings it back to life.  I can let it sit for a long time, but it's dead.  By contrast, if I ssh using PCLinuxOS, I can work normally within the ssh shell.  (Edit files, read text, run commands, whatever...)

I tried your suggestion with ssh -vvv and there is indeed very verbose output as the connection is established.  Once I do 'ls -la' however, the terminal freezes, and there is no further output.  Other things that cause the freeze: cat some file, run top, basically execute anything that generates text output.  Once a certain number of characters have been displayed the session freezes.

Other than the frozen ssh session, all other functions on the notebook work normally.  Web browsing, ftp, or any other network activity work normally.  Only the ssh session in the terminal freezes.  All other network traffic is flowing as normal.

---

### Post by kevdog on 2008-05-30
I take it when your client terminal freezes -- the actual server it is connected to does not freeze.  Seems like a challenging problem.  No wireless involved correct.  IPV6 deativated?

---

### Post by crashtest on 2008-05-30
> **kevdog said:**
> I take it when your client terminal freezes -- the actual server it is connected to does not freeze.  Seems like a challenging problem.  No wireless involved correct.  IPV6 deativated?

Yes, that's correct.  The server side is fine, it is the client that freezes.

I didn't have much time today to work on this, but I did boot a notebook from the live CD and connect to the same server from within the LAN, and the connection was perfect and did NOT freeze.  Which seems to take us back to issues with router hops, port forwarding, MTU sizes and so forth - but remember: from my home, running on identical hardware, from behind the same home router, and connecting to the same ssh server, PCLinuxOS works, and Ubuntu does not.

That said, I seem to remember reading that there is some sort of reverse DNS lookup going on when connected with SSH.  I will have to research this and see what the actual details are, as I am no doubt getting this completely wrong going by memory.  Could the problem be something as simple as a different /etc/nsswitch.conf setup, or some other hostname resolution issue?  The plot thickens...

---

### Post by psquared89 on 2008-07-01
Any progress on this? I have identical symptoms...

---

### Post by crashtest on 2008-07-04
> **psquared89 said:**
> Any progress on this? I have identical symptoms...

No progress to report.  Just for the hell of it, I tried ssh from the command line on MAC OS X (another machine on my home network)  SSH from the Mac works properly.  I know this proves very little, but it does help once again to eliminate firewall/router issues.  

Please keep me posted if you have any luck troubleshooting this issue.  Thanks.

---

### Post by crashtest on 2008-07-14
As another little experiment, I downloaded the PCLinuxOS Gnome 2008.1 Live CD.  Guess what?  This has the same problem as Ubuntu.  Tried the PCLinuxOS 2007 KDe live CD again to confirm, and ssh worked properly and did not freeze.

This couldn't actually come down to a KDE vs Gnome issue could it????

---

### Post by kevdog on 2008-07-15
A drastic proposal, however have you ever thought of compiling the ssh server/client from source.  Perhaps you have a bad client version and a newer version would help.  I know this seems extreme, but I don't think it will be that difficult given the fact of how much time you have put into the problem thus far.

---

### Post by clerum on 2008-10-07
Not sure where to purse this but while doing some IPv6 testing I'm seeing a similar issue. 

So far I have traced it down to the server sending packets which are larger (sometimes 2x) the size of the interface MTU of 1500.

Those who are experiencing this may want to check their packet sizes with a tcpdump.

Those more familiar with the nuts and bolts of the kernel, can you point me to the next step for troubleshooting and bug reporting...

Thanks

-C

---

### Post by bkieser on 2009-03-22
I have this problem with Konsole under Intrepid, Kubuntu. I can work, sometimes for hours, in ssh, then suddenly it will freeze. Almost always on output from the server. In fact, I don't think it's ever frozen the other way around.

I have switched to using Xterm and so far so good.

No comms problems anywhere else although Firefox 3 cannot post to about 50% of the sites that I use via https. So I am beginning to think that there is a problem with SSL, a weird data-related problem. To be precise, I think that there is a particular type of data or data contents that cause FF3 and Konsole/ssh to freeze/lock up.

This is backed up by the fact that I normally use more than one session and only 1 temrinal will lock up (to the same box using the same accounts), the others will work. But then randomly at various points another will go, then another...

So far not had any lockups on Xterm.

---

### Post by apmcd47 on 2009-03-22
> **crashtest said:**
> As another little experiment, I downloaded the PCLinuxOS Gnome 2008.1 Live CD.  Guess what?  This has the same problem as Ubuntu.  Tried the PCLinuxOS 2007 KDe live CD again to confirm, and ssh worked properly and did not freeze.

This couldn't actually come down to a KDE vs Gnome issue could it????

What version of ssh is on this live CD? I'm guessing 4.7p1 or later...

You never mentioned the version on your office server.

> **kevdog said:**
> A drastic proposal, however have you ever thought of compiling the ssh server/client from source.  Perhaps you have a bad client version and a newer version would help.  I know this seems extreme, but I don't think it will be that difficult given the fact of how much time you have put into the problem thus far.

... er, actually, I'd go for an older one - the 4.5p1 of the PCLinuxOS that worked, over the 4.7p1 that doesn't work on Ubuntu. Configure it to install and run under your home directory first - if it doesn't work just delete it. If it works, reconfigure it to run under /usr/local and remove the ssh package. If it is the version of ssh, you should consider sending a bug report to the maintainers of OpenSSH. You would need to give the version of the sshd on your server, too.

I've just looked at the OpenSSH web site and the latest release is 5.2, so manually upgrading to that is an option, but I'd try the older version first.

If you have control of the office server, I might suggest upgrading the server's sshd as well, or instead. In my opinion you have a client/server mismatch.

Andrew

---

