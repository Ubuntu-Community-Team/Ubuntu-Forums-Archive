---
title: "Bidirectional FTP Synchronize"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by jeffimperial on 2008-05-12
I'm a pretty recent convert to OSS in general and Ubuntu in particuler (OS at least).

With some ~2500 files to be processed each day, the Web designer that I am needs anything that resembles, even distantly, what *_Adobe Version Cue_* does. I've been trying to discover **Subversion** but I find it too partial to developer language. It's so _difficult to set it up_. So I'm looking for something with **[COLOR="Red"]GUI,[/COLOR]** not CLI.

Another difficulty is that I don't have Server Admin rights since I'm allowed to do  that only from the Workstation at the office (We're still in XP there, and I have migrated partially to Ubuntu at home). Hence, **[COLOR="DarkOliveGreen"]I only have FTP access[/COLOR]**, no SFTP or SSH. I want to do a little of the workload at home, but want to do it from Ubuntu to complete my migration.

Oddly enough, the **Server is a Linux machine**. Maybe that's a plus. I can connect to it via Places > Connect to Server... Service Type: FTP (with login). But manually doing the sync is way too much murder.

I have tried using **CrossFTP** and it can be used, but it's way too _cluttered_ with way too much overhead.

Suggestions will be very, very appreciated.

---

### Post by kevdog on 2008-05-12
A little off topic but ever heard of cygwin for windows?  Yes a linux emulator -- red hat specifically.  Gives you an ssh daemon.

Just an fyi.  If you know linux, you know cygwin.

---

### Post by jeffimperial on 2008-05-13
> **kevdog said:**
> A little off topic but ever heard of cygwin for windows?  Yes a linux emulator -- red hat specifically.  Gives you an ssh daemon.

Just an fyi.  If you know linux, you know cygwin.
Thanks for the FYI. And I don't see how this question is off topic. Anyways, I'm at a loss. I was looking for a way to synchronize my Ubuntu home PC to a remote server using FTP. As I have mentioned in the fairly lengthy post, I don't have SSH from home and server-side installations are a no.

I'm looking into CYGWIN. Thanks

---

### Post by kevdog on 2008-05-13
Again a little bit off topic -- cygwin can be installed and run from USB stick.  Or if you just need an ssh client from work, you could just use putty -- this is truly a portable app that is very small and can be run from a usb stick.  At home you would need a running ssh server.  

Although it would be somewhat inconvienent, what you could do if you have no server at work/cant install a ssh server on the computer/have firewall problems that wont let an outsider reach an inside computer due to a firewall -- would be to set up a reverse ssh tunnel from work -- which would mean log in from work to home -- you would need to keep the tunnel open (dont log out).  Then while at home you could use this open tunnel to then sync the contents from the home server to work.  It would even be possible for another computer on the home LAN to log into the ssh server computer (where this computer would simply pass the connection from the work to the other home LAN computer -- port forward).

A syncing program -- rsync, unison -- come to mind but there are others however, could then be run over this encrypted connection (totally secure), to provide the two way mirroring/or synchronization.  Only differences would be transmitted saving bandwidth.

Its possible also to run cygwin rather than putty from a USB stick, although I think the installation is roughly 2Gb so you would need a larger capacity flash drive.  Ive done this too and it also works.  Ive even done portable cygwin to a cygwin ssh server at home -- 2 Windows machines (before I was using Ubuntu) so I know that really a linux computer isn't needed -- only the OpenSSH utility.

---

### Post by jeffimperial on 2008-05-13
> **kevdog said:**
> Although it would be somewhat inconvienent, what you could do if you have no server at work/cant install a ssh server on the computer/have firewall problems that wont let an outsider reach an inside computer due to a firewall -- would be to set up a reverse ssh tunnel from work -- which would mean log in from work to home -- you would need to keep the tunnel open (dont log out). Then while at home you could use this open tunnel to then sync the contents from the home server to work. It would even be possible for another computer on the home LAN to log into the ssh server computer (where this computer would simply pass the connection from the work to the other home LAN computer -- port forward).

Again all this is under the assumption that I can access the remote computer using SSH, which I have already said twice that I do not. **ONLY FTP.**

Anyway, thanks for all the tips and info. I know these will help me later on as i progress with my use of Ubuntu. I have settled for CrossFTP Pro for now. It's basically another java-based FTP client with built in multi-directional sunchronization with automation feature and a somewhat usable GUI.

PS

And I still do not get how this thread is off topic :confused:

---

### Post by kevdog on 2008-05-13
Ok Im not trying to push you but I dont really understand??

Another difficulty is that I don't have Server Admin rights since I'm allowed to do that only from the Workstation at the office (We're still in XP there, and I have migrated partially to Ubuntu at home). Hence, I only have FTP access, no SFTP or SSH. I want to do a little of the workload at home, but want to do it from Ubuntu to complete my migration.

Ok -- so run putty or ssh client at work (no admin - just user rights needed) and then run the ssh daemon (server) at home (which it sounds like you do have admin rights??  Again reverse tunnel or simply tunnel from work to home, and there you go.  All you need. Except for the sync utility.  

Maybe I'm missing something.  There is nothing wrong with FTP.  Its lightweight fast and easy.  However Im really paranoid about security.  FTP transmits in clear text.  Easily readable.  Basically no security.  SSH (SCP) is the rich man's FTP -- little overhead.  In fact if you need a window's client that runs on top of putty take a look at WinSCP (its a GUI and really easy!!) [http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

Just tossing around some ideas and really trying to understand your situation.

---

### Post by curran on 2009-02-04
I'm in the same situation as jeffimperial - I want to synchronize a local directory in an Ubuntu desktop with a remote directory over FTP. I do not have SSH access. The synchronization utility is all I want.

I can connect to the remote directory and view it as a folder in Nautilus with the path [ftp://user@ftp.website.com/remotedirectory](ftp://user@ftp.website.com/remotedirectory), so I can copy files myself very easily, but I need automatic synchronization.

Unison seems like the perfect tool for the job, but unfortunately it doesn't support FTP. I'm looking for some way to execute something which has the effect of

unison ./localdirectory [ftp://user@ftp.website.com/remotedirectory](ftp://user@ftp.website.com/remotedirectory)

Rsync also supports SSH but not FTP, so it seems I can't use RSync either.

Does anyone know a way to get Unison or RSync to work over FTP? or any other similar open source synchronization tool that supports FTP?

Thanks very much for your help.

---

