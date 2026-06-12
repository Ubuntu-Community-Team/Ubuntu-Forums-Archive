---
title: "Setting up PPPoE wired connection in Ubuntu 18.04.1 Bionic Beaver (Desktop Version)"
date: 2018-08-31
forum: Networking &amp; Wireless
---

### Post by araghuramindia on 2018-08-31
My ISP provides PPPoE connection with username, password and service  name and binds my MAC Address. Since I have connected my router to the  WAN, the MAC Address of the router has been bound in their server by  them. The IP address, Gateway and DNS addresses are automatically  obtained.  My Desktop has been connected to the router and the network  is working fine.


  However, for the purpose of troubleshooting the network when it goes  down, I need to connect directly to the computer. Therefore, I need to  know how to configure a wired PPPoE connection directly in my computer.  The network settings GUI does not allow setting up one.

  
Please guide me how to -

  
1) configure a PPPoE connection
2) specify the username, password and service name, and
3) clone my router's MAC address to my desktop

  
to be able to connect to the internet.

  
After referring to various community posts, I tried the following command:

nmcli connection add con-name "..." type pppoe username ... password ... service ... parent .... autoconnect no ifname "*" save yes

The  pppoe connection gets created but vanishes from the "Settings -> Network" GUI under "Wired" category after some time.  Also, neither the command nor the GUI, allows me to specify a cloned MAC address.

It would have been better if there was a GUI for this.

  
Looking forward to the HELP, as I am not quite conversant with Linux commands.

---

### Post by praseodym on 2018-09-01
Please try
```

sudo pppoeconf
```
Add your username and PW and answer all other questions with Yes or Ok

---

### Post by araghuramindia on 2018-09-01
WIll it allow me to clone my NIC's Mac Address with that of the Router, so that I get connected to my ISP's server. 

Morever, it is mentioned in some community posts that 'PPPOECONF' conflicts with 'NETPLAN' under Ubuntu 18.04, which is what I have.

---

### Post by praseodym on 2018-09-02
If its not working, revert it via
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and reboot.

---

### Post by araghuramindia on 2018-09-03
pppoeconf didn't work and I had to revert back.

---

### Post by bret-a on 2018-12-26
I don't think the MAC is as important as the login info.  You can call you ISP and they will give it to you.  You may be able to find some or all of the info in your router/modem's web GUI.

---

