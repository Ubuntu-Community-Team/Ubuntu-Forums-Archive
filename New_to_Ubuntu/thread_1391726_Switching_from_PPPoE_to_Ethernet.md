---
title: "Switching from PPPoE to Ethernet"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by karthikophobia on 2010-01-27
I use a pppoe connection at home and I need to switch to ethernet connection at work. So please tell me how to configure and switch.

earler I had a similar problem and I used to move the files in /etc/network/interfaces and it used to work but I can't find that location now.

I use karmic 64-bit

Thank you

---

### Post by bullgr on 2010-01-27
normaly you right-click in the network icon in the taskbar and manage your connections...

you said that you want to connect to your work thru ethernet... you need to know from the admin (if any) at your work the ip, subnet mask and ip...

for example, in my network i have these options in my pc:

ip: 192.168.1.3
subnet mask: 255.255.255.0
gateway: 192.168.1.100
DNS: 192.168.1.100

take these info from the guy how manage the network at work and put them in your network manager (like i said above, right-click in the network icon in the taskbar)...

---

### Post by shreepads on 2010-01-27
> **karthikophobia said:**
> I use a pppoe connection at home and I need to switch to ethernet connection at work. So please tell me how to configure and switch.

earler I had a similar problem and I used to move the files in /etc/network/interfaces and it used to work but I can't find that location now.

I use karmic 64-bit

Thank you

Can I suggest you change your ADSL modem setup at home to handle the PPPoE connection for you. This works out much simpler as you just plug in and go at either place...

Apologies if you have already considered and ruled out this option!

---

### Post by karthikophobia on 2010-01-27
> **shreepads said:**
> Can I suggest you change your ADSL modem setup at home to handle the PPPoE connection for you. This works out much simpler as you just plug in and go at either place...

Apologies if you have already considered and ruled out this option!

Could you kindly guide me on setting up the ADSL connection.

When I first connected to my pppoe connection, I read about 'pppoeconf' and followed.

plz forgive my stupidity and help me

thank you

---

### Post by shreepads on 2010-01-28
> **karthikophobia said:**
> Could you kindly guide me on setting up the ADSL connection.

When I first connected to my pppoe connection, I read about 'pppoeconf' and followed.

plz forgive my stupidity and help me

thank you

Well that really depends on which make of ADSL modem you are using as each of them do this a little differently. A little bit of RTFM of the modem plus the instructions below should help.

Basically
- Login to the modem's admin console (usually by pointing your browser to [http://192.168.1.1](http://192.168.1.1))
- Default user/ password is usually admin/ admin (again this depends on your modem make)
- Go to the 'Setup'/ 'WAN Connection' or 'ADSL connection' or something similar
- You should have connections called something like PVC0/1 etc setup there, which would be of type 'Bridged'
- Create a new one of type 'PPPoE' provide all the parameters that you do in pppoeconf there, leave any you don't understand to default
- If there is a DHCP option switch that on
- Save, as say PVC2
- Delete the old one
- Save the modem config to firmware and reboot
- When the modem starts up again, if there is a separate 'PPPoE' status light it should come on
- In Ubuntu network admin just use a default LAN connection to connect

Ideally once you login but before you make any changes, use the option to save the config to a file on the desktop, which you can later upload to go back to your old config if anything gets screwed up.

---

