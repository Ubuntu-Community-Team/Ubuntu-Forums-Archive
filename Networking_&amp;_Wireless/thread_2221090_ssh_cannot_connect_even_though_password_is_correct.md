---
title: "ssh cannot connect even though password is correct"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2014-04-30
So I'm trying to connect to the laptop from another machine with SSH. I've done this a million times before. This is a new install of Kubuntu 14.04 with openssh-server installed. On the laptop, I can connect to localhost with my login password. But when I try to connect from the other machine, it keeps rejecting my password. The machine has a static IP address assigned to it and no other machines are using the same IP address. In fact, the laptop has 2 static addresses, one for a wired connection and one for the wireless. Trying to connect to the wired IP addr, it just hangs. Trying to connect with the wireless IP address and it rejects the password every time. 

Where do I go from here?

---

### Post by nothingspecial on 2014-04-30
Do you have password authentication set to no in you config file on the server ?

---

### Post by scottbomb on 2014-04-30
No, I didn't change anything in /etc/ssh/sshd_config. The line in question still says #PasswordAuthentication yes

It does prompt me to enter my password, it just tells me it's wrong every time. It's the same password I log into the computer with every day. This is a fresh install of 14.04 on both machines. The laptop can ssh to the main machine but not the other way around. Sitting at the laptop, I can ssh to localhost and it accepts the password fine. It's only when trying to connect from other machine does it say my password is incorrect.

By the way, none of these failures are being logged in /var/log/auth.log
Very strange.

---

### Post by scottbomb on 2014-04-30
I did an arp-scan and it's reporting the same MAC address for both the wired and wireless ports on the laptop! Not possible. The laptop 's ifconfig does report a different MAC for each. The router (tomato firmware) has both ports too. Very puzzling.

---

### Post by scottbomb on 2014-04-30
After unplugging the laptop from ethernet and letting the laptop run on wireless only, I was finally was able to connect. I wonder if there is a bug somewhere that should filed. This is very strange behavior and should not be occurring.

---

