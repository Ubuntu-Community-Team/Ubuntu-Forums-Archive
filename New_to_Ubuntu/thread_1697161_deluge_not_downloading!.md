---
title: "deluge not downloading!"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by mick_86 on 2011-02-28
i have downloaded deluge to download torrents, but when i open the software the torrents dont seem to be downloading. some of the torrents seem to be finding seeds and peers but still not downloading. any ideas?

also my internet connection is fine.

thanks for any feedback in advance.

---

### Post by aktiwers on 2011-02-28
Are you behind a proxy or firewall or somethink like that?

Did any other torrent app work?

---

### Post by mick_86 on 2011-02-28
> **aktiwers said:**
> Are you behind a proxy or firewall or somethink like that?

Did any other torrent app work?

no proxy and don't think there is a firewall in place. don't know if there is any settings i need to adjust? still new to this, only installed ubuntu a week ago.

edit: forgot to say tried transmission but that just shut down my net any time i tried to start downloading.

---

### Post by aktiwers on 2011-02-28
Before you used Ubuntu, did torrent apps work?

I'm just trying to find out if your ISP is shaping your connection or if you need to open ports in your router.

Often you can bypass ISP's traffic shaping, but enabling full encryption in the torrent client.

---

### Post by mick_86 on 2011-02-28
> **aktiwers said:**
> Before you used Ubuntu, did torrent apps work?

I'm just trying to find out if your ISP is shaping your connection or if you need to open ports in your router.

Often you can bypass ISP's traffic shaping, but enabling full encryption in the torrent client.


yes before i installed ubuntu torrent apps worked fine, for well over a year at least.

---

### Post by TechWiz2100 on 2011-02-28
Check forwarded ports. I think Ubuntu is not very good at using UPnP so you have to forward them manually.

---

### Post by mick_86 on 2011-02-28
> **TechWiz2100 said:**
> Check forwarded ports. I think Ubuntu is not very good at using UPnP so you have to forward them manually.

how do i go about doing that?

---

### Post by synapsys on 2011-02-28
> **mick_86 said:**
> how do i go about doing that?

You will need to configure Deluge to use a certain port (in Deluge settings,) and then open up that particular port on your firewall/router. Be advised that any time you forward a port from the Internet to one of your internal addresses, you are potentially opening up a hole in your defenses for hackers to use. I highly suggest you read up on the consequences of doing this before you mess with your configuration. That being said, you can go to this website to learn how to forward a port through your router:

[http://portforward.com/]("http://portforward.com/")

---

### Post by mick_86 on 2011-02-28
> **synapsys said:**
> You will need to configure Deluge to use a certain port (in Deluge settings,) and then open up that particular port on your firewall/router. Be advised that any time you forward a port from the Internet to one of your internal addresses, you are potentially opening up a hole in your defenses for hackers to use. I highly suggest you read up on the consequences of doing this before you mess with your configuration. That being said, you can go to this website to learn how to forward a port through your router:

[http://portforward.com/]("http://portforward.com/")

ok went to my ip adress and gave deluge the same permissions as bittorrent, now its downloading fine. thanks very much for all your help!! appreciate it it.

---

### Post by mick_86 on 2011-02-28
ok now its stopped working again. went to my ip adress, allowed deluge through by copying bittorrent permissions and it worked for maybe 5 minutes. at the bottom of the deluge window it says no incoming connections.

and also now when i try to go to my router settings via my ip address the page wont load.

does anyone have any idea what i need to do?

---

### Post by TechWiz2100 on 2011-02-28
I'm not quite understanding your terminology here. What do you mean by "my ip address"? You router should have its own IP address and if its no longer responding to its own IP then you might need to reboot it. If torrents are crashing your router you need to limit the number of connections and/or bandwidth.

---

### Post by mick_86 on 2011-02-28
> **TechWiz2100 said:**
> I'm not quite understanding your terminology here. What do you mean by "my ip address"? You router should have its own IP address and if its no longer responding to its own IP then you might need to reboot it. If torrents are crashing your router you need to limit the number of connections and/or bandwidth.

OK sorry, i'll try and explain myself better, just read back my post and it barely makes sense to me.

first of all i was having trouble using transmission for my torrents, it was crashing my net connectivity for my laptop as well as my ps3. 

i uninstalled that and installed deluge, when i tried to download my torrents through deluge it was finding seeds and peers but wasn't downloading. i took the advice of trying to forward the port through my router which i did by typing in my ip address into my address bar, which came up with the menu i needed for this. i get my internet from BT and use a bthomehub2.

forwarding the port like this worked for a round 5 minutes and now isn't working, at the bottom of the window it says that there is no incoming connections. to top that off now my wireless stops working every few minutes, then just starts working again a few minutes later.

when i try to get back to my menu by typing in my ip address the page just times out.

hope that makes it a bit clearer, any advice would be appreciated.

edit: also when my net crashes for these few moments, i have my torrents stopped so they are not trying to download.

---

### Post by TechWiz2100 on 2011-02-28
Check if other devices are having connectivity issues with the same network. If they are they you must reboot the router and you may want to consider getting a new one because it seems torrent traffic is overloading it.

To avoid overloading it you might either want to limit your torrent's combined upload and download speed to 80% of total throughput and further limit upload to about 80% of that to ensure your download speeds don't suffer too much. Also limit the number of connections and half open connections. 

I had this issue a lot with my old Belkin G router and a Netgear N router. Haven't have trouble with Buffalo yet other than the fact that it requires you to use IE for configuration of the wireless so configuring it from Ubuntu is a no-go unless you can suffer having IE on Wine.

---

### Post by mick_86 on 2011-02-28
> **TechWiz2100 said:**
> Check if other devices are having connectivity issues with the same network. If they are they you must reboot the router and you may want to consider getting a new one because it seems torrent traffic is overloading it.

To avoid overloading it you might either want to limit your torrent's combined upload and download speed to 80% of total throughput and further limit upload to about 80% of that to ensure your download speeds don't suffer too much. Also limit the number of connections and half open connections. 

I had this issue a lot with my old Belkin G router and a Netgear N router. Haven't have trouble with Buffalo yet other than the fact that it requires you to use IE for configuration of the wireless so configuring it from Ubuntu is a no-go unless you can suffer having IE on Wine.

the hub is quite old, might phone them and see if i can get a new one, i have my laptop connected up to the net by cable and everything is working fine with that, so i'm sure its a wireless issue.

thanks everyone for your feedback, much appreciated. its good to know theres a community here to support newbs like me, i like what ive seen of ubuntu so far and much better than win 7(which i'm pretty sure broke my old laptop all by itself), just need to get a better understanding of how it all works.

---

### Post by TechWiz2100 on 2011-02-28
> **mick_86 said:**
> the hub is quite old, might phone them and see if i can get a new one, i have my laptop connected up to the net by cable and everything is working fine with that, so i'm sure its a wireless issue.

thanks everyone for your feedback, much appreciated. its good to know theres a community here to support newbs like me, i like what ive seen of ubuntu so far and much better than win 7(which i'm pretty sure broke my old laptop all by itself), just need to get a better understanding of how it all works.

The best of luck to you in your endeavors with Linux my friend. In terms of reliability, I find linux to be top notch regardless of the distro so even if you leave Ubuntu you can probably expect the same quality of experience.

---

### Post by synapsys on 2011-03-01
> **mick_86 said:**
> .

first of all i was having trouble using transmission for my torrents, it was crashing my net connectivity for my laptop as well as my ps3. 

forwarding the port like this worked for a round 5 minutes and now isn't working, at the bottom of the window it says that there is no incoming connections. to top that off now my wireless stops working every few minutes, then just starts working again a few minutes later.

when i try to get back to my menu by typing in my ip address the page just times out.


It definitely sounds like your router is dying. I've had this same experience with a few wireless routers when they are near the end of their useful life. The wireless radio will start to cut in and out until it stops working all together. If you are sure that all your settings in Deluge are correct, and all your ports are properly forwarded, I would say you definitely need a new router. I've been using Deluge for awhile and it works great!

---

### Post by mick_86 on 2011-03-01
thanks synapsys, ive had my laptop wired to the router since last night now and there has been no problems since, deluge is working fine and so is my normal net. thanks for the help guys.

---

