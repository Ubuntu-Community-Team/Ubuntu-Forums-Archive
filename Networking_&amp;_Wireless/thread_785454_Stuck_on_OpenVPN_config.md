---
title: "Stuck on OpenVPN config"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by DarrenRBaker on 2008-05-07
Hi all,

I'm attempting to configure OpenVPN using the [HOWTO]("http://openvpn.net/index.php/documentation/howto.html#pki") found on their site, and I keep running into a problem nobody else seems to mention. It's during the step where I create certificates, and I've copied the sequence of events below:

```

darren@monolith:/etc/openvpn/easy-rsa/2.0$ . ./vars

NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/2.0/keys

darren@monolith:/etc/openvpn/easy-rsa/2.0$ sudo ./clean-all
[sudo] password for darren:

Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.

darren@monolith:/etc/openvpn/easy-rsa/2.0$ sudo ./build-ca

  Please edit the vars script to reflect your configuration,
  then source it with "source ./vars".
  Next, to start with a fresh PKI configuration and to delete any
  previous certificates and keys, run "./clean-all".
  Finally, you can run this tool (pkitool) to build certificates/keys.

```

Not sure what the problem is here, but I'm banging my head against the wall. Has anybody encountered this?

Thanks,

Darren

---

### Post by stefan197504 on 2008-05-17
hi,

now i know how to post. you have to complete the registration.

once more for all.

it will work with "sudo /bin/bash" and then all command of course without sudo.

think it got something to do with the standard-shell. but im not sure about it.

greetings 
stefan

---

### Post by bloodniece on 2008-05-20
I think you have to run

```
source ./vars
```before this will work

---

### Post by slack42 on 2008-06-20
Same problem here. I've done source ./vars but still get that message.

---

### Post by slack42 on 2008-06-20
Hi, I don't know if this thread is still alive but I figured out this problem. I looked in the vars file and saw that one of the variables it was creating was export PKCS11TOOL="pkcs11-tool". I checked to see if I had pcks11-tool installed and I didn't so I did some googling and found that it was part of opensc. I installed that package and libopensc2 as well, just in case. One of them worked and now I have pkcs11-tool installed.

Then I went back to the directory and went threw the process of setting up the certificates again but this time I did two things different. First I became root with "sudo -s" and then I created the keys directory because it looked like it wasn't being created for some reason.

Once I did that I went threw the steps again and when I did ./build-ca the script finally worked and presented me with the questions that the [HOWTO]("http://openvpn.net/index.php/documentation/howto.html#pki") on the openVPN page said that it would. I also had to do one last thing. When I tried to add the certificates with network-manager-openvpn plugin I couldn't because all the keys where owned by root. So I had to change the owner of them with "chmod -R me keys/".

Hope this helps someone, it was very frustrating for me to figure out why this wasn't working. I haven't connected to the VPN yet so I don't know if I did everything right but at least I was able to get all the certificates created. Connectiong to the VPN will be the next challenge.

---

### Post by uzi09 on 2009-02-11
I believe this might have been mentioned earlier as well, but basically for me it worked without having to install anything else.

It was just giving problems if you tried to use sudo to run the commands. Switch to the root user and do the steps. There are various ways of doing that. I personally prefer:
```
sudo su
```

Hope that helped someone out.

EDIT: Sorry, forgot that I created the keys directory as well

---

