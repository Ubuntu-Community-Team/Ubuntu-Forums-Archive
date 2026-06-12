---
title: "Ubuntu server 9.10 - remote access  from outside the localnetwork"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by gottijr on 2010-03-11
-linux newbie-

  I've just build this home server with Ubuntu server 9.10

  And i have open ssh on it.

  I've made a static ip 192.168.*.*
  
  Question is ... if i want to access my server from outside the network with putty or NX how will i do that?

  what is my server ip than?

  pls advice for a newbie in linux and server so me and maybe others can use this thread.

  thank you in advance

---

### Post by Daveski on 2010-03-11
Be careful exposing your machine to the public internet. If you have a router you will need to forward the ssh port (22) to the 192.168.x.x local address that your server has. You should search and read about port forwarding and the potential security risks this may pose.

Also check this thread:
[http://ubuntuforums.org/showthread.php?t=1427509]("http://ubuntuforums.org/showthread.php?t=1427509")

---

### Post by Locke_99GS on 2010-03-11
> **gottijr said:**
> what is my server ip than?

After following Daveski's advise, you would access your server at the address given to you by your ISP. This can be found in your router's main page, or a website such as [http://www.whatismyip.com](http://www.whatismyip.com) .

edit: Many ISP's provide your dynamic public IP on lease, and leases usually last two days. (or until DHCP asks for another) You can use a service such as provided by DynDNS.com to give you a free subdomain for your IP, and linux tools to automatically update their service so that your address always points to your IP.

---

### Post by gottijr on 2010-03-11
So i think one of the steps would be to creat SSHOpenSSHKeys - private and public key!

  Let's assume A is the server B is the windows pc with putty.

  how this works?

---

### Post by gottijr on 2010-03-11
I'm trying to do the port forwarding

  So i accessed my wireless router -> Applications & Gamming

  and i have this options now (pls advice)

          port range

  Application	Start	End	Protocol  IP Address	Enable
       *          *      *         *          *           *

---

### Post by Locke_99GS on 2010-03-11
Application "SSH"
Start "22"
End "22"
Protocol "TCP"
IP Address - Use the local address of your server.
Enable "check"

---

### Post by gottijr on 2010-03-11
> **Locke_99GS said:**
> Application "SSH"
Start "22"
End "22"
Protocol "TCP"
IP Address - Use the local address of your server.
Enable "check"

   when you come with so simple answers makes my questions looks so stupid:)

  thanks

---

### Post by WorldTripping on 2010-03-11
An easy way to access files on the server is to use sshfs. 

sshfs 111.111.11.1:/server/directory /remote/machine/directory

(If you have set up port forwarding correctly.)

Where 111.111.11.1 is the IP address of your router.

/server/directory is an existing directory on the server.

/remote/machine/directory is an existing directory on an outside machine.

HTH

---

### Post by gottijr on 2010-03-11
> **Daveski said:**
> Be careful exposing your machine to the public internet. If you have a router you will need to forward the ssh port (22) to the 192.168.x.x local address that your server has. You should search and read about port forwarding and the potential security risks this may pose.



   would you like to advice about security options? things we should keep in mind?

   for ex what is the secure way to ssh from A (windows - putty) to B (ubuntu server) outside local lan?

  thanks

---

### Post by alfplayer on 2010-03-11
> **gottijr said:**
> would you like to advice about security options? things we should keep in mind?

   for ex what is the secure way to ssh from A (windows - putty) to B (ubuntu server) outside local lan?

  thanks

I think OpenSSH is very secure, you don't need to worry anymore unless you have very high security expectations. To improve security a bit you could change the default port number (22) to any unused port number that you choose. Also, it is obviously important to use strong passwords.

---

### Post by gottijr on 2010-03-11
> **alfplayer said:**
> I think OpenSSH is very secure, you don't need to worry anymore unless you have very high security expectations. To improve security a bit you could change the default port number (22) to any unused port number that you choose. Also, it is obviously important to use strong passwords.

 I've generator a key with puttygen (rsa)

 I've put the pub to authorized_key in ./ssh

 how do i enable the service for sshkey?

---

### Post by alfplayer on 2010-03-11
> **gottijr said:**
> I've generator a key with puttygen (rsa)

 I've put the pub to authorized_key in ./ssh

 how do i enable the service for sshkey?

Do you want to connect using PuTTY? Look for an option on the PuTTY interface to enable keys.

---

### Post by gottijr on 2010-03-11
i found some good tutorial for ssh keys

  puttygen

 [http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html]("http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html")

  ssh key on ubuntu server

  [http://www.howtoforge.com/set-up-ssh-with-public-key-authentication-debian-etch]("http://www.howtoforge.com/set-up-ssh-with-public-key-authentication-debian-etch")


  there's one more question left:

  i think my server ssh is set for ssh2 dsa how can i change to ssh1 rsa?

  pls advice

  p.s. i guess this is my problem cause putty says can't load private key (on ssh1 rsa)

---

### Post by alfplayer on 2010-03-11
Are you trying to use SSH version 1? Keep in mind that SSH2 offers more security and is now the default and recommended version.

---

### Post by gottijr on 2010-03-11
ok thanks than

  i guess is not needed anymore!

---

### Post by alfplayer on 2010-03-11
> **gottijr said:**
> ok thanks than

  i guess is not needed anymore!

You don't need it? OK then.

---

### Post by gottijr on 2010-03-11
> **alfplayer said:**
> You don't need it? OK then.

  thanks alfplayer

  one more day one more issue figure out!

  can you please advice if there is any other security issue of accessing my server from outside the local lan?

  thank you

---

### Post by alfplayer on 2010-03-12
You're welcome.

I've just found this excellent guide about securing OpenSSH: [http://wiki.centos.org/HowTos/Network/SecuringSSH]("http://wiki.centos.org/HowTos/Network/SecuringSSH")

---

