---
title: "DavFS2 is driving me crazy!!!"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by mingohills on 2008-10-01
I am running Hardy trying to mount a Windows server via davfs2. I have already dealt with the GUI "Connect to Server" work around connecting to godaddy's onlinefilefolder, that is using the "Location" function of Nautilus and typing 
davs://<server>

I would then be prompted to give user name and password.  

However when I tried the same process with our office server, it simply says "Unauthorized" and fails to mount.

After failing using fusedav in the terminal I tried using davfs2.

I installed the davfs2 1.2.2 3ubuntu1 package through Synaptic and then 
-ran the reconfiguration tool 

-fixed /etc/davfs2/davfs2/config to match the groups entered into the reconfig 

-edited /etc/fstab to connect to my specific server

-edited secrets file to carry my username and password (also tried to mount without "secrets" holding username and password) 

When I run username@mycomputer$ mount /mnt/location

It prompts me for a proxy login, I hit Enter and it runs my info stored in secrets.

This is the output.

```
Please enter the username to authenticate with proxy
http or hit enter for none.
Username: 
/sbin/mount.davfs: connection timed out two times;
trying one last time
/sbin/mount.davfs: server temporarily unreachable;
mounting anyway

```

But that is not true!!!!  I have been on the phone with the administrator while I am trying to mount.  

I wanted to upgrade to the davfs2 1.3.3 provided on sourceforge.net but I am not sure this will help, and besides I can get it to install anyway because it won't recognize my neon library.  

I am totally frustrated.  I just want to mount a server via webdav protocol!!!!  

Please help me!!!

---

### Post by mingohills on 2008-10-01
Ok.  So I stripped out everything and started over completely.

Also I added the option "nouseproxy" to the line in /etc/fstab

it now reads 
https://<server>  /home/myname/mnt davfs rw,nouseproxy, user 0 0

NOW.  I get through login, but I get this 

> /sbin/mount.davfs: the server certificate does not match the server name
/sbin/mount.davfs: the server certificate is not trusted
  issuer:      07969287, [http://certificates.godaddy.com/repository](http://certificates.godaddy.com/repository), GoDaddy.com, Inc., Scottsdale, Arizona, US
  subject:     Domain Control Validated, <server>.com
  identity:    <server>.com
  fingerprint: ***********************************
You only should accept this certificate, if you can
verify the fingerprint! The server might be faked
or there might be a man-in-the-middle-attack.
Accept certificate for this session? [y,N] 

I say yes and get this 

> /sbin/mount.davfs: Mounting failed.
GSSAPI authentication error (Unspecified GSS failure.  Minor code may provide more information: No credentials cache found)


I tried saving the cert in a the /etc/davsfs2/certs file and /home/myname/.davfs2/certs

I also edited the config files in the directories to with 
servercert /path/to/cert

still no good.

I do have one other thought the cert was named mail.<server>.com I added a pem extensition so it reads mail.<server>.com.pem


I am getting the Linux blues bad.  Please help.

---

### Post by mingohills on 2008-10-02
So following the work around advice of several other threads.  This is what I did.

Installed Konqueror.
Make sure that webdav and webdavs protocols were enabled.  Open Konqueror GUI then go to

Settings>Configure Konqueror...>Previews and Meta-Data

Click the radio button for Internet Protocols (unless you have a reason to limit the your protocol use.  Then just enable webdavs)

Then just type in your server location in the address bar with the appropriate protocol.

Like So.
> webdavs://myserver.location/folder/name


You should be prompted with a dialog box and 
Voila!!  You can choose split screen under Window> for easier click and drag so you don't have to fiddle with Nautilus windows.   

The only problem so far is that I cannot directly open any Ooo files on the server (because it is not technically mounted!!) 

(I found a work around that explained I needed to mount the server and navigate under Konqueror.  Yeah, if I could mount it I wouldn't have this problem!!)

However, that just means that you have to copy a version onto your local harddrive and edit from there, then copy/overwrite back to the server folder when you are done.  

Hope this helps anyone with the same issues!!!!!


I am learning yay!!!

---

### Post by jimvach on 2008-11-16
Hi, read your thread, very interesting.

I have a webdav share on a local ubuntu 8.04 server, which is protected with basic auth/htpasswd. I have Slax on an EeePC which connects fine through Konqueror with rw permissions. So far so good....

I also have a Dell running ubuntu 8.10. Using GUI Places>Connect to Server... with all credentials correct returns "not authorized".

So lets try the c line...

mount -t davfs [http://192.168.2.100:80/webdav](http://192.168.2.100:80/webdav) /media/WebDAV

asks for credentials, and then mounts the share, but read only, I have tried -o rw with no luck...

however, cadaver 

apt-get install cadaver

a c line dav program mounts the share with full rw privs

I would prefer not to go down the route of installing a new file browser to get this to work. Why is DAV so half baked in Ubuntu?

---

### Post by mingohills on 2008-11-17
It is getting worse.  So I had a hdd failure.  I decided I would take the plunge and installed Intrepid.  Now I am back to square one.  I want to mount a secure server via webdavs.

 I have tried every trick imaginable.
1. "Connect to Server. . ." under Custom Location.  No go. Says to change viewer.

2.  I tried using davs:// protocol in nautilus location bar.  Access Denied"

3.  I have tried davfs and it gives me the same message I have posted before.

4.  Cadaver freezes up completely.

5.  Fusedav nothing.

6.  I installed Konqueror again, much to my dismay.  However, under Hardy, Konqueror was my best solution.  Now, nothing.  "Connection to Server Interrupted" 

It is not the server because, on my girlfriends windows machine, I have easy access, with click and drag, etc.  I love my Ubuntu but this webdav is killing me.  

I work from home and I need access to that server on a very regular basis.  At this point i either work directly on her computer (not a happy camper) or I have to access my files via firefox, download them, save, share, to a folder on her computer and at the end of the day I migrate my shared folder to the server from her computer.  

Please tell me someone has an answer.  I am getting very frustrated.

Is it certificate issue?

I am just guessing at this point.

Thank you for any help in advance!!!

---

