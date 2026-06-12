---
title: "Connecting two home ubuntus"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by thepopasmurf on 2008-08-13
I have two laptops with ubuntu on each, each laptop has a wireless connection to the internet, how can I access the files on the other computer or how can I set up a shared folder?

---

### Post by eddVRS on 2008-08-13
I would suggest openSSH- This allows you to access the files and directories on the other laptop via the text based terminal.

Install on both machines (sudo apt-get install openSSH)(I think)
run the server on one, and connect with the client on the other... You can then transfer files across the wireless network.

When I get home, I'll get you all the details unless someone beats me to it or has other suggestions.

---

### Post by Krydahl on 2008-08-13
I followed the instructions [here]("http://https://help.ubuntu.com/community/SettingUpNFSHowTo") and didn't have any problems.

---

### Post by eddVRS on 2008-08-13
Great stuff... You got it working? I use this all the time to remotely admin my other PCs.

Use scp to transfer files-
Scp usr@192..x.x.x/source/dir /target/dir 

Lemme know if you need anything else

---

### Post by thepopasmurf on 2008-08-13
Okay I've installed the server and client versions of openSSH on both computers, now what?

---

### Post by eddVRS on 2008-08-13
get both machines up and running-

open a terminal on the server machine and type: ifconfig
note the internal IP address (something like 192.168.0.) 

on the client machine open a terminal and type:

ssh usernamehere@internalIPaddresshere

The user name needs to be a valid user name on the target/server machine.
eg. mine would look like this: 
ssh edd@192.168.0.5

it will ask for a password, this is the password for that user on the server machine.

Let me know if I've been unclear, or if you run into trouble

---

### Post by Krydahl on 2008-08-13
Personally I prefer NFS - that way you can mount the share directory and use nautilus to access it.

---

### Post by eddVRS on 2008-08-13
I've not tried that. Reason I opted for SSH was so that I could fire commands up to a pair of headless servers I run
might give it a go though

---

### Post by Krydahl on 2008-08-13
Hmm - guess which is better in this case depends on how the laptops are connecting. The OP says he has two laptops with connections to the internet. If they're getting to each other via the internet, NFS probably wouldn't be too secure. In my case the machines are using a private network so it's not such an issue.

---

### Post by eddVRS on 2008-08-14
> **Krydahl said:**
> <snip>you can mount the share directory and use nautilus to access it. I think you can do this with SSH also- under places > connect to server > top dropdown menu to SSH, and fill in user name...

---

### Post by thepopasmurf on 2008-08-14
Thank you all, the SSH is working great

---

### Post by thepopasmurf on 2008-08-14
Another quick question, I have one computer connected to a printer, is there a way I can use that printer from the other computer using SSH or something else.

Thanks again in advance

---

### Post by user440 on 2008-08-14
> **Krydahl said:**
> I followed the instructions [here]("http://https://help.ubuntu.com/community/SettingUpNFSHowTo") and didn't have any problems.

Too many hypers in your hyperetext.  Correct URL here: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by eddVRS on 2008-08-14
> **thepopasmurf said:**
> Another quick question, I have one computer connected to a printer, is there a way I can use that printer from the other computer using SSH or something else.

Thanks again in advance

Glad it's worked for you. I'll have a read up on the printers... Thing is; I don't have any printers connected to my PCs at home (paper free :D )

---

### Post by Krydahl on 2008-08-14
See if I can do a link correctly this time.

You don't need anything to complicated to share the print - it can be done via the GUI

see [here]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu").

---

