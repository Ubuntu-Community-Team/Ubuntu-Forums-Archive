---
title: "Internet sharing with a network cable"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by Muni Beduhin on 2008-01-02
Jan 2 08

I should probably start with this question:
Is it even possible to network to computers with a regular network cable, or do you need a special crossover cable?
If the answer is that it is not possible, I need not go farther. Actually, about how much would a crossover cable cost and how reliable would the networking between the setup below be?
If it is possible, how do I do it. Or if I need a crossover cable, how do I do it?

I have a laptop with Ubuntu 7.04 that wireless accesses a network that allows it to get on the internet. (My laptop does have an ethernet port). Guidedog and openssh-server are installed.
I also have a desktop with Kubuntu 7.10 which has an ethernet card but not wireless card. I would like to give it access to the internet through my laptop. It does not have openssh-client. (It was originally Kubuntu 7.10 w/ KDE 4.0 rc1 and though I have reverted to KDE 3.5.8, it still has some quirks.) However, I could always install whatever I need by moving the DEB packages over via external USB drives.

I have searched all around on the Ubuntu Forums and Google and learned some things but not enough to get this working.

I am reasonably comfortable with CLI but would rather use a frontend than a long string of commandlines because I've noticed that the frontends tend to figure things out for you and work better.

Any help would be appreciated.

---

### Post by Predator[23rd] on 2008-01-02
Hi!

[QUOTE=Muni Beduhin;4058470]
Is it even possible to network to computers with a regular network cable, or do you need a special crossover cable?[QUOTE]

It is possible. If you use a switch/hub with auto sensing you can do it with any ethernet cable you have. If you only want to use a single cable and directly connect two computers it has to be a cross-over cable.

Cross-over cables are almost the same price as normal ones. But if I were you I would get myself a simple 4 or 8 port switch and two cables ...

Setting up a home network is easy too:
Configure your laptop's and desktop's ethernet cards so that they are in the same subnet.
Assuming both named their ethernet cards *eth0*, you do that by editing the */etc/network/interfaces* file to look like this here:
[I]
auto eth0
iface eth0 inet static
  address 192.168.1.100
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255


auto eth0
iface eth0 inet static
  address 192.168.1.101
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  gateway 192.168.1.100
[/I]

first one is for your laptop, second one for your desktop.

Since you prefer GUI elements install a firewall with graphical user interface, FIRESTARTER for example. Run the FIRESTARTER wizard to enable internet connection sharing.

once your are done, restart your network (**sudo /etc/init.d/networking restart**) and if necessary firewall.

that should do the trick.

---

### Post by Muni Beduhin on 2008-01-03
Many thanks. That should give me enough info to pull it off whatever way I decide to go.

---

