---
title: "no wired after file system error"
date: 2020-10-21
forum: Networking &amp; Wireless
---

### Post by kuraiskrap on 2020-10-21
running a minecraft server, we seem to have some SSD stability issues, i assume related to the SSD

but we had a file system error and after running Fsck on it to correct it
we had no wired ethernet listed in the GUI
someone gave me some commands to try in terminal but they didnt work

the ethernet is whats built into the 
[COLOR=#000000]B550-f strix wifi[/COLOR]
[https://www.asus.com/ca-en/Motherboa...-GAMING-WI-FI/]("https://www.asus.com/ca-en/Motherboards/ROG-STRIX-B550-F-GAMING-WI-FI/")

the commands and such he had me run

ip link show
[IMG]https://media.discordapp.net/attachments/674003261472374825/762054880051200000/unknown.png?width=587&height=48[/IMG]
cat /etc/os-release
[IMG]https://media.discordapp.net/attachments/674003261472374825/762056033014513704/unknown.png?width=613&height=179[/IMG]
sudo ifconfig enp7s0 up
[IMG]https://media.discordapp.net/attachments/674003261472374825/762058057173303347/unknown.png?width=820&height=34[/IMG]
ifconfig
[IMG]https://media.discordapp.net/attachments/674003261472374825/762059354052231229/unknown.png?width=498&height=244[/IMG]
sudo netplan apply
[COLOR=var(--text-normal)][FONT=Consolas]nmcli
[/FONT][/COLOR][IMG]https://media.discordapp.net/attachments/674003261472374825/762070799066202112/unknown.png?width=411&height=50[/IMG]
[COLOR=#DCDDDE][FONT=Consolas]nmcli networking on
[/FONT][/COLOR]
the above were his troubleshooting ideas, and whats been done thus far.

anyone got any ideas?

---

### Post by TheFu on 2020-10-21
First, please don't post images. Use the copy/paste and post text here. People who use screen readers or pay by the byte for internet will thank you.

B550-f strix uses a new Intel Ethernet NIC, the v225. This isn't well supported and a number of people here have failed to get it working.  In theory, the drivers directly from Intel should work, but 3 people here tried those and failed.  I know 2 ended up buying older Intel NICs based on the e1000e or igb drivers to get something working quick for about $25 in solution.

Wish I had better news.  Last month I almost bought that same B550 motherboard, but after doing some research on the v225 support, decided to wait and if necessary, get an Asus B450 STRIX using the i211 NIC instead.

I'm confused.  You say "server", but also say "GUI".  Servers don't have GUIs.  They use text files to configure network settings. Look in /etc/netplan/ for the configuration. Post those files.

Also, seeing the hardware and driver in use for the NIC would confirm some other stuff.  There are many different methods to get that information. lshw, lspci, inxi ... I'd use:
```
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
```

Whenever posting files here and commands+output, please wrap all the text in  'code tag', as I've shown above.

---

### Post by Skaperen on 2020-10-21
what were your [COLOR=#0000ff][FONT=courier new]**umount**[/FONT][/COLOR] and [COLOR=#0000ff][FONT=courier new]**fsck**[/FONT][/COLOR] command lines?

---

### Post by kuraiskrap on 2020-10-21
yeah so the reason they were images is they were taken from a discord chat log already had them as images. apologise for having them consume more data

as for the nic, we already ordered one, i figured if i can get it working its atleast redundancy

we are using it for a server but installed the desktop because we couldnt get the networking to work via terminal

my linux experiance is also fairly limited so having a GUI is easyer depending on what i have to do, saves me having a 2nd PC to google everything i need to do anything

i dont remember doing umount commands but the fsck commands was basicly
fsck /dev/nvme0np1
or something whatever it said in the recovery mode after the reboot, pretty sure its just the drive name

---

### Post by TheFu on 2020-10-21
I don't think that adding a gui to a server install brings in all the low, deep, stuff, like network controls.  Use the text config files like it is a server. The ubuntu server guide should have instructions. There are a number of netplan posts in these forums too.

But the v225 driver could still be an issue. Hopefully not.

I really hope you didn&#8217;t run fsck on a drive.  t should be run on a file system, which is usually a partition.

---

### Post by kuraiskrap on 2020-10-22
i ran fsck on whatever was listed when i ran it in recovery mode, it did fix the issue so i didnt worry much

and yeah no the GUI is trash compared to windows, because linux expects you to use terminal to do basicly everything, but for basics its easyer for linux noobs like me.

---

### Post by kuraiskrap on 2020-10-24
SO update, i messed around with a few things and did manage to bring it back, i THINK it was because i set the renderer to Network manager

[COLOR=#000000][FONT=Whitney]/etc/netplan/01-netcfg.yaml[/FONT][/COLOR]

  renderer: NetworkManager

it came up, during me installing a 2nd nic, but it also broke the internal ports for our Docker and stuff i dont understand so we reversed it without checking the original port, but it did show in the GUI
this is more in case someone stumbles upon it

i also ran a bunch of things we may of edited at the time

sudo netplan apply
systemctl reload NetworkManager
sudo service network-manager restart

im uh, REALLY bad at linux, but im not running a server off wifi now so thats a plus

---

