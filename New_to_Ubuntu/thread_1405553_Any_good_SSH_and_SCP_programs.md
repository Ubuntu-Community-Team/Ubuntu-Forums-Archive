---
title: "Any good SSH and SCP programs?"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-12
Hi again!
I need an SSH and SCP program for some of my school projects. What they told us to use was WinSCP. Can I use some other program - native linux - and what would it be?

---

### Post by falconindy on 2010-02-12
man ssh
man scp

---

### Post by lockalidiot on 2010-02-12
Any with GUI?

---

### Post by 2hot6ft2 on 2010-02-12
I had to look up WinSCP to see what it was...;)

Would ssh do what you need to do. I can transfer files in dual pane like a ftp program and a lot more. See the link in my sig below and look at the screen shot at the bottom of the How To page for SSH FreeNX DD-WRT.

For the dual panel krusader or the How To: Nautilus Dual Panel Karmic/Juanty also in my sig

---

### Post by mixmastamyk on 2010-02-12
Try the Places Menu/Connect to Server...

I believe if you choose the ssh service-type option, you will able to mount the server as a disk and then use nautilus instead of a fugly gui like winscp.

Kubuntu probably has something similar.

---

### Post by 2hot6ft2 on 2010-02-12
> **mixmastamyk said:**
> Try the Places Menu/Connect to Server...

I believe if you choose the ssh service-type option, you will able to mount the server as a disk and then use nautilus instead of a fugly gui like winscp.

Kubuntu probably has something similar.
That would be krusader

Tranferring files using a GUI (Graphical User Interface) like nautilus or krusader

Nautilus (Ubuntu)
Places > Connect to server
Service Type: SSH (or FTP, Public FTP, Windows Share, WebDAV, Secure WebDAV)
Server: IP Address of the server
Port: The port you set the server to
Folder: /home/<your-user-name-on-the-server>/

Click on Connect

krusader (Kubuntu)
Tools > New Net Connection
Protocol: fish:// (other options available)
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer

Click on Connect

I'm not sure how or if it can be done with Konqueror

---

### Post by lockalidiot on 2010-02-12
Thank you for answers! The Connect to Server option works, sort of... I just don't recognize the view I get... Typical windows convert I suppose: "This doesn't look familiar...":P
I'll see to the other option now.

---

### Post by 2hot6ft2 on 2010-02-12
You can install krusader with
```
sudo apt-get install krusader
```
then it will be in
Applications > Accessories > Krusader
Krusader looks a lot like Total Commander

---

### Post by marshmallow1304 on 2010-02-12
When I used Windows, I loved PuTTY.  I don't use it any more because I just use the ssh command, but it is available in the repos: [putty]("apt://putty").

If you're using nautilus, you can also type
```
ssh://user@ip.address:port/
```
in the address bar.
The user@ is unnecessary if it's the same on server and local machine.

---

### Post by bcn17 on 2010-06-19
The package *sshfs* is what I prefer for GUI /w ssh. 


To mount the remote filesystem 
```
sshfs -p <port number here> externalIPaddress.com:/directory/of/folder/on/remote/machine /home/username/folder_remote_system_will_reside_in
```

To unmount:
```
fusermount -u /home/username/folder_remote_system_will_reside_in
```

---

### Post by DavePlummer on 2010-06-19
If you are uncomfortable with sshfs and Nautilus, try [FONT=Lucida,Verdana,Helvetica,Arial]gFTP.
[/FONT]

---

