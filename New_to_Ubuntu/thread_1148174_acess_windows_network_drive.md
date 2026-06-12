---
title: "acess windows network drive"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by 1234 on 2009-05-04
I wanted to acess a windows network drive under ubuntu how could i determine the local ip addresses of the pc inorder to mount it. and what are the commands to mount it on my pc.

---

### Post by Alterax on 2009-05-04
> **1234 said:**
> I wanted to acess a windows network drive under linux how could i determine the local ip addresses of local machines inorder to mount them. and what commands to use to mount.

Well, you could use the smbmount command, but there's an easier way.

Go to Places > Connect to Server.
On Service Type, choose Windows Share.

For server, put in the IP address of the box (or its hostname if you have a local DNS server).  You can get that from the windows box by opening the windows command prompt and running the ipconfig command.

Back on your 'buntu box. put the name of the fileshare in the Share box.  You'll also need a username and password from the Windows box that has access to that share.  Domain I wouldn't worry about unless you're actually using one.

Then click OK and it'll mount the share for you.

---

### Post by Alterax on 2009-05-04
Now that we're not traipsing all over the forums for the same question, I'm not sure why the command prompt is locked out of the windows computer.  Generally the administrators will give you access if you need access.  That you don't have access or an IP address might be taken to mean that the administrators don't want you to remotely access that machine.  You might have to ask them for permission and addresses, then plug it into the formula I listed above.

The only other option I can tell you is that you can scan your entire network segment with nmap, looking for an open port 139 (NetBIOS), 445 (mainly used by Windows directory services) or 3389 (Remote Desktop protocol).  IPs that have these ports open are usually Windows boxes.

Note that port scanning IS detectable, and in many cases is considered a type of passive attack.  So if it's not your network, this could be a violation of terms of service (and in some municipalities or networks could be considered criminal activity) so be careful and get permission first.  It's a lot better to just ask the admins sometimes rather than trying to be sneaky.

---

