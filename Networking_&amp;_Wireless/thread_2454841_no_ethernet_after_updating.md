---
title: "no ethernet after updating"
date: 2020-12-07
forum: Networking &amp; Wireless
---

### Post by pepe13 on 2020-12-07
Hi, I&#7743; on kubuntu 20.04, discover alerts me on every update wich I installed frequently. The point is my ethernet connection is gone and I am unable to recover it

this is /etc/network/interfaces file contents

auto enp3s0
iface enp3s0 inet static
address 192.168.0.112
netmask 255.255.255.0
gateway 192.168.0.1

have to say that now I was able to get internet to work again running sudo dhclient enp3s0, but dont know if this is a correct config or if I have to type it every time I usa linux.

another thing I have noticed is that the icon in the task bar is now in blue color

[IMG]https://ibb.co/5sMKTrw[/IMG]

sorry, image is here [https://ibb.co/5sMKTrw](https://ibb.co/5sMKTrw)

any advice ? 

thank in advance

---

### Post by SeijiSensei on 2020-12-07
I think /etc/network/interfaces may now be deprecated under systemd.  Try renaming it to interfaces.bak and rebooting.

You should then be able to right-click the network icon in the panel ("task bar") and choose Configure. You'll be taken to a dialog where you can specify the IP information if you prefer manual addressing.  Otherwise it should default to DHCP and give you the same results you got when you ran dhclient.

---

### Post by pepe13 on 2020-12-07
yes, I prefer static ip, up to the moment I was running with same config as interfaces is showing, but configured in the applet in the task bar, but for some reason it stopped working.

ok, i´ll come back with results. thank you

---

### Post by TheFu on 2020-12-07
**netplan** took over in 17.10 from the old ifupdown /etc/network/interfaces.  Use that to configure static IPs if you want that done outside some GUI.

---

### Post by pepe13 on 2020-12-09
Well, as I was unable to get it to work i planned to fresh install 20.04 and tachan, impossible to get ethernet to work, as in previous system.

I tried installing 18.04, and now everything works well, even though after some updates, I am again in the first post. Ethernet stopped working again.

Do you have aby clue on what is going on?

I just tried setting up /etc/netplan/0something.yaml file but the command sudo netplan try gives an error message, aborting. So I am still with no connection at all, even sudo dhclient enp3s0 wich allowed me to connect to the net isn't now working either.
Any help, please?

---

### Post by TheFu on 2020-12-09
Perhaps if you posted the 0something.yaml , exact commands used AND output using _code tags_, someone could help?  
We cannot read minds.

Without 'code tags', yaml file indentation is lost here, so that is mandatory, required. YAML files are indentation sensitive.

---

### Post by pepe13 on 2020-12-09
I understand but I wont be able to exact copy the yalm file cause i dont have internet connection in this machine, well, the computer shares a windows installation, do you think saving the file to a windows partition and open it from there would do the job?
 Wich editor is best to open it and share it with you?

---

### Post by TheFu on 2020-12-09
I'm confused.  If you boot into a *Try Ubuntu* environment (say from a flash drive), does networking not just work?

Copy the file to some flash media, but we need to see the commands too. How to capture those commands and the output is explained in this link: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) You'll be using redirection.

Retyping is NOT an option. We need to see the actual files with the actual commands AND the actual output, as they are, unmolested.

I can't comment on what Windows may or may not do. Sorry.

Any true editor should work, but you don't need that, since you'll be using sneaker*net.  [https://en.wikipedia.org/wiki/Sneakernet](https://en.wikipedia.org/wiki/Sneakernet) Hopefully, you'll boot into a Try Ubuntu environment, insert the flash drive and copy/paste the contents here.  No need for Windows anything.

---

### Post by pepe13 on 2020-12-09
> **TheFu said:**
> I'm confused.  If you boot into a *Try Ubuntu* environment (say from a flash drive), does networking not just work?
no, it doesn´t

> Copy the file to some flash media, but we need to see the commands too. How to capture those commands and the output is explained in this link: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) You'll be using redirection.

Retyping is NOT an option. We need to see the actual files with the actual commands AND the actual output, as they are, unmolested.

what commands are you asking for? when I tried this ? ```
sudo netplan try
```

> I can't comment on what Windows may or may not do. Sorry.
no problem with that

> Any true editor should work, but you don't need that, since you'll be using sneaker*net.  [https://en.wikipedia.org/wiki/Sneakernet](https://en.wikipedia.org/wiki/Sneakernet) Hopefully, you'll boot into a Try Ubuntu environment, insert the flash drive and copy/paste the contents here.  No need for Windows anything.

uploading the yaml file will do the job? I dindn´t realised this way and I´ll surely do it this way, not at home right now, but will be back with all you need, thank you

---

### Post by pepe13 on 2020-12-10
for some reason I am now unable to boot to kubuntu, so I´ll try to fresh install again, if the problem reproduces, Ill come back. Sorry for the inconvenience and thank you very much

---

