---
title: "ssh from a remote computer into my laptop"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by aliyanage on 2007-06-13
Hi all,

I would like to be able to ssh from a remote computer into my laptop at home. Now what I've done so far is to get a dyndns account and open a dynamic dns account and also I configured it on my router at home.

What exactly do I have to enable or to configure on my laptop to be able to ssh from a remote computer anywhere else in the world? could somebody please give me some tips or solutions for this one?


thanks
aliyanage

---

### Post by anywebloco on 2007-06-13
The very basics are this:
1)You need ssh installed and running on your laptop. On my Kubuntu Feisty installation this is done by typing the following in a terminal:
> sudo apt-get install ssh
2) You need an ssh client on the remote computer - Putty is the standard Windows client ([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/))

---

### Post by aliyanage on 2007-06-13
Thanks for the reply... I just installed ssh... thought that's installed by default. But another thing that I would like to know is whether there is something else that I have to configure on my laptop meaning like port or so that the remote computer is able to ssh into my laptop via a certain port?

regards
aliyanage

---

### Post by Vorbis on 2007-06-13
Na, that should be you. ssh runs on port 22, most things including PuTTY with default to that.

Another thing could be to make sure your laptop is open on port 22 to the internet, and your router isn't stopping any TCP traffic on that port.

D.

---

### Post by anywebloco on 2007-06-13
The default port is 22. If you have nmap installed then you should be able to tell whether sshd is running on port 22.> nmap 127.0.0.1 -p22You can change the port in /etc/ssh/sshd_config but if you do, you'll need to restart sshd.

---

### Post by aliyanage on 2007-06-13
okay how do I start, end or restart ssh services? I opened up port 22 on my router/firewall and installed ssh using this command:

sudo apt-get install ssh

and is there a way I can test it out myself from my laptop?

---

### Post by vanadium on 2007-06-13
By default, the ssh client is installed. You need to install openssh-server (synaptic) though to enable your laptop to accept ssh connections.

---

### Post by aliyanage on 2007-06-15
okay I've got everything set now so that basically it should work. Also I've tested the the remote connection to my firewall/router... which was working and I've setup the port forwarding to ssh into my machine...

now my question is whether I have to some kinda start openssh  / ssh itself before I start testing it or whether it automatically should be running/working after startup.

does anyone know...?

---

### Post by t4thfavor on 2007-06-15
If your using the openssh-server, it will be running at boot. 

On my laptop all i did was forward the port for ssh to the outside, and install openssh-server. And it was working after that.

Make sure your ISP is not blocking port 22, 

best practice is to forward port XXXX whatever to port 22 on the laptop then use the client on port XXXX. That saves you from automated brute force attempts.

---

### Post by kevdog on 2007-06-15
For the server (or your laptop), it needs to run the ssh daemon -- which is the program accepting connections.  After installation this should automatically run at boot, or you can stop,start,restart program by:
sudo /etc/init.d/ssh start  or stop  or restart

Beyond that you need to make private and public keys for yourself or whatever user is going to log into the computer.  I think the command is:
ssh-keygen -t rsa -b 2048

This command by default will make private and public keys in the ~/.ssh directory.  I believe (Im not in front of my machine right now, so this is just from memory, the names of the files are id_rsa (private key) and id_rsa.pub (public key).  You need to copy the public key into your authorized_keys file: (within ~/.ssh directory)
cat id_rsa.pub >> authorized_keys


If the daemon is started (I believe it should be, if not start as stated above), test configuration on server by:
ssh localhost

---

### Post by aliyanage on 2007-06-29
okay guys,

thanks a lot for the information, I found out it was an issue with the setting I've made on my wireless router. I've made a small manual for all of those who have a similar setup on my website, so be free to visit :-D

[www.mindexchange.ch](www.mindexchange.ch) and then go to Network


Thanks a lot again for the help, appreciate

---

### Post by herrdoktor330 on 2007-07-25
I'm going to ask a straight up n00b question.

ssh is for opening a terminal to a remote machine, as if you had a terminal open on your "home" box? if that's the case, then this article is answering my question.

I'm wondering. I want to make a new computer using ubuntu server and I wanted to tuck it away in a closet and remote administer it that way: by command line only.

---

### Post by az on 2007-07-25
> **herrdoktor330 said:**
> I'm going to ask a straight up n00b question.

ssh is for opening a terminal to a remote machine, as if you had a terminal open on your "home" box? if that's the case, then this article is answering my question.

I'm wondering. I want to make a new computer using ubuntu server and I wanted to tuck it away in a closet and remote administer it that way: by command line only.

Correct.  That is the typical way to run an Ubuntu server.

---

### Post by herrdoktor330 on 2007-07-25
> **az said:**
> Correct.  That is the typical way to run an Ubuntu server.

OK... so to recap, because I'm a little daft sometimes:

Installing an ssh server will allow you terminal into your linux box and run command line commands on that remote box.

If that's the case, I found the right thread for my project. Now all I have to do is get better at command line linux operation.

If there's anything else I'm missing from this equasion, please let me know.

---

