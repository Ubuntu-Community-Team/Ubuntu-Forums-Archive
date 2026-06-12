---
title: "How to SSH into my Laptop?"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by chipwhisperer on 2007-06-18
hi everyone,

I'm running Edgy and I have a dilemma which I could use help with. i just got a job where i cannot take my laptop to work, but the job requires some stuff that I will need from my laptop. So, I thought a good solution would be to SSH into my laptop. However, I have no idea how to set this up. I install ssh with the command:

sudo apt-get install ssh

but I'm lost from there. I hear it's really simple, but I'm kinda confused. Does anyone have a tutorial link or know how to set it up?

Thanks so much for any help!

---

### Post by A*p on 2007-06-18
You will need to install the openssh-server onto your laptop and setup port forwarding port 22 on you router to the internal network IP address of your laptop.

---

### Post by nymphaeles on 2007-06-18
Think about a usb thumb drive unless you want through the thrill of setting up an openssh server in your laptop.

---

### Post by A*p on 2007-06-18
Here is a link to a Linux Reality podcast that will help you quite, there is plenty on the net about ssh but this will get you up to speed on the bits you need to know.

[http://www.linuxreality.com/podcast/episode-37-ssh/](http://www.linuxreality.com/podcast/episode-37-ssh/)

---

### Post by A*p on 2007-06-18
Installing the ssh server is not a chore it is as easy as typing **sudo apt-get install openssh-server** as well as been an incredibly useful tool,  it is far more secure than a thumb drive that can get lost or stolen.

---

### Post by kevdog on 2007-06-18
Ill try to find a tutorial for you, but rest assured its really easy.  Setting up the server is really easy.  If you need to make changes the configuration file is found at /etc/ssh/sshd_config.  

In addition to the server you are going to have to install software on the client machine to access the server.  This by far Ive found to be the harder part.  If your client machine is windows, you can use putty or cygwin.  Of course if the client machine is linux, I think the ssh program is built in.  You will need to make public and private keys, and install the public key on the server.  This is easy also, however you will probably need a walkthrough the very first time you do it.

If you give me more ideas about operating systems the server and client are running it would be more helpful.  Both ssh servers and clients can be installed on windows/linux machines.

---

### Post by chipwhisperer on 2007-06-18
hey everyone,

thanks for the quick replies! however, some questions:

1) I got the SSH into my local machine to work by:

ssh localhost

and that worked fine, but how do I start up the daemon? If I log in to an account, and just leave it open, will that suffice?

2) do I need to install anything special to allow X-fowarding? i've used it a ton to SSH into other machines, but I dont know if it needed any special software.

3) since I'm ssh-ing into a machine not on my local network, I know I can do it by IP address. However, and this is a n00b question, is that just the ip address that one has while browsing the web, such as would be seen at this site: [http://www.whatismyipaddress.com/](http://www.whatismyipaddress.com/)

If so, would the command just be (for example):

ssh -X <user>@199.12.322.122

thanks again everyone, you've all been tremendously helpful!

---

### Post by chipwhisperer on 2007-06-21
Hi everyone,

I actually answered all of my own questions. Thanks again to everyone! LinuxReality is a great podcast, by the way.

---

