---
title: "Alternate/secondary IP"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by naja74 on 2008-03-12
Hey guys, I'm looking for info on how to setup a secondary IP in ubuntu. I dual boot my laptop between XP and Kubuntu, and use both at work. I have XP setup to pull DHCP when it can, but I also have a secondary static address setup if it can't get DHCP. Some of our satellite networks are DHCP, while my main area is still static. 

I'm looking to setup Ubuntu the same, so I don't have to reconfig my interface every time I take it out to one of these satellite locations and then reconfig it when I get back. It's not that big of a deal in itself to reconfig, but it's getting annoying having to do it several times a week.

Any ideas?

Thanks,

Naja74

---

### Post by SpaceTeddy on 2008-03-12
mhm, i have an idea, but it is not "directly" what you might want... it's not really a secondary ip confguration, it is just a command that will overwrite your network settings with static stuff (this is temporary until you use network manager again or reboot)

to temporay configure a network device, you can use
```
sudo ifconfig eth0 up 192.168.0.2 netmask 255.255.255.0
```

change the device, ip and subnet to whatever you need.

next is that you need to your default gateway - this can be done via
```
sudo route add default gw 192.168.0.1
```
where 192.168.0.1 is your default gateway - again, fix this to match your settings.

last, you need dns servers - these are kind of permanent, so i would sugget you save your old config file, create one that is for your current location and when you are done, write the old one back - to create one, you could use 
```
sudo mv /etc/resolv.conf /etc/resolc.conf.save
echo -e "nameserver 192.168.0.1\nnameserver 10.0.0.0" > /etc/resolv.conf
```

the first line saves your current config, the second will write a new config with the needed nameservers for the current location. (the \n in there means newline - just leave it in and fix the ips.)

to revert the config, you can use this command
```
sudo mv /etc/resolv.conf.save /etc/resolv.conf
```

Now, putting it all together so you do not have to type all all the time. 
in your .bashrc, you can define command aliases. Also, you can join commands by using  ; as the seperator.

so, lets say you want a static config called sat1, you would put the following command in your .bashrc (add the line at the end)

> alias sat1="sudo ifconfig eth0 up 192.168.0.2 netmask 255.255.255.0; sudo route add default gw 192.168.0.1; sudo mv /etc/resolv.conf /etc/resolc.conf.save; echo -e "nameserver 192.168.0.1\nnameserver 10.0.0.0" > /etc/resolv.conf"

the next terminal you open will know the command "sat1" and will apply the settings you have put in the command - you can define as many of them as you want...

i would also encourage a command that unconfigures your network. This is not really needed, since a dhcp offer will even write back your nameservers properly (overwriting the manual changed), but it might be nice to have one anyway
could look like this
```
alias undef="sudo ifconfig eth0 0.0.0.0; sudo mv /etc/resolv.conf.save /etc/resolv.conf"
```

one last note - if you use the manual configs, it might be neccessary to switch off network manager for that time - i am not sure about it - but there is a possibilty.

I don't know if that is what you acctually had in mind, but that is how i configure my stuff for static networks :)

---

### Post by naja74 on 2008-03-12
Thanks Space!!

---

