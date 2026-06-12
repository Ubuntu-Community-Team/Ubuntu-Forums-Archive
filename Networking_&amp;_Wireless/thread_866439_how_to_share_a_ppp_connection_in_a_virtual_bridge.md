---
title: "how to share a ppp connection in a virtual bridge ?"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by alsdkjhf23465 on 2008-07-21
hello everyone!
i am having some difficulty setting networking up the way i want in my ubuntu laptop...

here is the situation:
i have a server pc at home running linux (slackware) i have set it up as an openvpn server...

 now on the laptop side which is the focus here:
laptop has an ethernet iface and a wireless one (eth0 and eth1 respectively)...
additionally i have installed virtualbox binaries and created a windowsXP session... i also read in the help menu that if i want the winxp running on vbox and the ubuntu host to see each other over samba , i should create a virtual bridge on the host, and include in it the ethernet iface and then use some VBoxAddIF script to create a virtual driver to be used my winxp session in the 'host interface' field... and bring it under the bridge to

finally i have a gprs modem (from my mobile) which i use to connect to the internet....its a pp connection...

what i want to do is basically:
- when im home i usually connect wirelessly to my home network...
- then if i wanna do some huge file transfer i connect the ethernet 
- finally when im out of the house i want to connect to the internet from the mobile

so far:
i have managed to connect to the internet from my mobile and use it to set up an ssh session through the Very strict proxy server of my mobile service provider, to my home... only on port 443 (https) i could manage that..

i have also managed to set up the virtual bridge between the linux host and the winXP (through the vbox driver)...
in /etc/network/interfaces 
i use the vbox suggestion:
auto br0
iface br0 inet dhcp
   bridge_ports eth0

what i CANT do:
-im not sure whether i should give the virtual bridge a static ip... and i dunno how to do that, evern though i have tried to read examples on briddging...

-important: whenever i start the bridge and the vbox driver i cant connect through ssh to home server anymore... 
- i want to share this ppp connection - when established with the virtual bridge, so that whenever i get internet on the linux host (and i get to ssh to my home that is) ill be able to share with winxp too the ppp connection...(how should i set u pthe interfaces file?, (i mean if this is the network config file, where is eth0 and eth1 setup????? i only see the loop back in there)

thank you in advance for your help..
any poiters/ guide and alternative configs will be appreciated..
thank you
nass

---

### Post by dmizer on 2008-07-22
your setup sounds way complex.  it might help to have a network diagram because i'm not exactly sure what you want to do, or where your problems are.

i believe this is what you have working:

home
<-wireless-> | eth0? ubuntu server br0 | virtXP
(internet works for virtualbox XP)

i believe this is what you would like to get working:

roaming
<-ppp-> | gprs modem | <=USB?=> | ppp0? ubuntu server br0 | virtXP
(internet does not work for virtualbox xp)

in this case, i see no need to configure eth1 for anything as nothing is connected to it.  but i'm also not sure exactly what devices are connected, and how they are connected when you're using your gprs modem.

however, if the above is correct then you are using a different network interface on the ubuntu server when roaming with your gprs connection.  if that's the case, then you would need to bridge that connection as well (br1), and that should show up as a second network connection in your virtualbox XP.

still hazy about your configuration though.

---

### Post by alsdkjhf23465 on 2008-07-22
truth is even though i feel  i know enough linux essentials on slackware where everything is manual, i seem to lose track of things in the automated ubuntu..

what i have is what i started with, when installing ubuntu, i started with eth0 (ethernet) and eth1 (wireless).. i can use any of the 2 at home to connect to my 192.168.0.0 home network
and to surf the internet...

then i installed vbox.... if i use the NAT option for the ethernet iface (or the wireless iface), then  guest OS sees all the pcs in my home network and can surf the net, but the home network can not access the guest OS... so then i read about using a host interface and i went on to read the vbox help menu...

there it stated that i should create a bridge in the /etc/network/interfaces config file, and add the physical network interface in there... i assumed that the ethernet iface would be the one to add in the bridge... then add a vbox virtual interface using some vbox tools (VBoxAddIf) to that bridge and use that to start up the guest OS with... i did as such and voila i managed to obtain the missing step from before; that is to be able to access the guest OS from all the other pcs in my home network... and have internet too of course... i did not automate these steps so i had to do them everytime i start up the pc.

finally i went mobile and started using my mobile phone to connect to the internet...there is a catch here.. the service provider wouldnt give it away from free, but only through a very strict proxy server setup.. so i had to use this non-transparent proxy server address.... 
i also connected it to the pc and i managed to have internet on the pc too! great so far (btw i could ssh over the mobile internet connection (using ProxyCommand in /etc/ssh/ssh_config) to my home too which was great)... but when i would go ahead and start up the bridge again , add the eth0 and the vbox0 iface in it i would stop having internet access.. ... basically know trying to ssh to my home would return a fatal error.
FATAL ERROR: failed to begin relaying via HTTP..

so i figure ... if i can have internet on the ubuntu host os without the bridge and vbox stuff... there should be a way to have the internet with those stuff too!

and the Q is how do i do it??:)
i dont care if its purely manual way... i can deal with it...
thank you for your help
nass

---

### Post by nanda_justgames on 2009-10-08
Have the same issue.

VBox... want to make a server. Set it up as bridge in virtual machine.. can acess the internet with my VM, but cant share folders with SAMBA

---

