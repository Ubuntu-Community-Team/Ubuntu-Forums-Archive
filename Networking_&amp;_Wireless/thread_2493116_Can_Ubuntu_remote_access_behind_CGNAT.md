---
title: "Can Ubuntu remote access behind CGNAT?"
date: 2023-12-04
forum: Networking &amp; Wireless
---

### Post by kotgc on 2023-12-04
[COLOR=#000000][FONT=&quot]Remote access on the home network used to work with Ubuntu's VNC and Remmina on a remote laptop.
However the ISP's CGNAT stops it working.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]From reading, a VPN or tunnel might be needed?
Is there an easy setup using remote access with Ubuntu?[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I tried OpenVPN but it needs a public WAN IP.
I've started looking at TailScale, but it's all new to me.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Just a simple home network solution would be good if a free VPS or something is needed?[/FONT][/COLOR]

---

### Post by TheFu on 2023-12-04
Easy?  No, but that depends on your definition of "easy".

TailScale is is probably the easiest, but real enterprise firewalls will still block it.

I have a paid VPS that runs my wireguard server to make connections for some public services possible. I do it this way, though I have a static subnet on the internet because it lets me have cheaper internet by 1/3rd.  

I used openvpn for a long time. It is complex and significantly slower than wireguard.  Also, wireguard makes using a VPN on my tablet and phone when away very easy.

---

### Post by kotgc on 2023-12-09
I'm trying TailScale for now, however whilst setup and connection was easy and actually 'just worked'!, it's not clear how to view and control the GUI?
OpenVPN failed as it needs a public WAN IP to issue a certificate.
Might try WireGuard if I can't solve TailScale's remote viewing and control.

The VPS and 1/3rd Internet cost sounds intriguing.

May I ask how you use your Tablet and Phone? Via GUI or CLI. CLI control seems straight forward using SSH and commands, however I'm aiming for GUI control.

---

### Post by TheFu on 2023-12-09
Please use default fonts and colors.  If you didn't go out of your way to change them, then your browser is doing it. Please make it stop.

> **kotgc said:**
> [COLOR=#0C0D0E][FONT=-apple-system]I'm trying TailScale for now, however whilst s[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]etup and connection was easy and actually 'just worked'![/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system], it's not clear how to view and control the GUI?
OpenVPN failed as it needs a public WAN IP to issue a certificate.
Might try WireGuard if I can't solve TailScale's remote viewing and control.
GUI? What GUI?  I've never used tailscale. I don't like using 3rd party services, especially if they have no financial reason that makes them WANT to treat me how I'd like to be treated.

> **kotgc said:**
> The VPS and 1/3rd Internet cost sounds intriguing.
That isn't what I wrote.  You've taken the numbers and misinterpreted them.

> **kotgc said:**
> May I ask how you use your Tablet and Phone? Via GUI or CLI. CLI control seems straight forward using SSH and commands, however I'm aiming for GUI control.[/FONT][/COLOR]

There's a wireguard app for android.  It is basically a toggle - on/off. I used a QRCode that I generated on my servers to make the Android client setups trivial. For Android, I don't use the VPS wireguard.  It is only to provide access back to my LANs where I have email, websites, a personal cloud, personal  wallabag (a "read-it-later" server) and about 20 other LAN services for use inside the household.  Wallabag has a client for android that syncs with my server, so changes made from any device are shared across all device views.

I avoid cloudy services ... so I don't need to worry about them being shutdown, as google tends to do with 80% of their best services.  OTOH, I get to maintain those servers, backup the data, etc.

---

### Post by kotgc on 2023-12-09
? all Ubuntu Desktop colours are default.

because it lets me have cheaper internet by 1/3rd.

I'm confused?
I'm using TailScale, which is connecting to this Ubuntu Desktop.
I then turned on Ubuntu VNC Share Remote Desktop and installed RealVNC on my phone, but still fails to view the GUI?

---

### Post by QIII on 2023-12-09
TheFu was talking about the Forum default font and color.  You were using an Apple font and had color tags.

I have reset the font and color in your posts.

---

### Post by kotgc on 2023-12-10
Well I'm using a work around now with a remote access client and server.
Bit confusing why I need a VPN or Tunnel, apart from security right?
Even when a VPN or Tunnel is installed, I haven't been able to setup remote viewing, say with VNC and RealVNC on the phone.

---

### Post by TheFu on 2023-12-10
> **kotgc said:**
> because it lets me have cheaper internet by 1/3rd.

I'm confused?

"Cheaper internet by 1/3rd" isn't the same as "1/3rd the cost."
Say I'm paying $100/month (I wish it was only that much!).  Cheaper by 1/3rd is $66/month, but 1/3rd the cost is $33/month.

> **kotgc said:**
> I'm using TailScale, which is connecting to this Ubuntu Desktop.
I then turned on Ubuntu VNC Share Remote Desktop and installed RealVNC on my phone, but still fails to view the GUI?

[LIST]
[*] Ubuntu Desktop is terrible for remote desktops. Use a lighter DE, say XFCE or LXQt or even Mate. Don't use Gnome. It doesn't work.
[*] A phone?  Seriously?  The screen is too small. Even an 8inch tablet screen is too small for remote desktops, but as long as it is 768p+ resolution, it should work ... but never for Gnome.  Gnome is a hog.
[*] VNC isn't secure either for authentication or network encryption, so you need a VPN or ssh-tunnel to access it.  The same usually applies to RDP because MSFT keeps trying to fix their security issues by making RDP encryption proprietary.  For a remote desktop, there is an easier way to access Linux desktops remotely. Use a protocol that leverages ssh and has a highly optimized VNC.  The tool that provides that is called **x2go**, but to my knowledge, it doesn't have an android client. The protocol used is called "NX" - at a high level it is ssh+compressed VNC. ssh is used for authentication and security, compressed VNC is used for the desktop and can be tuned to work using very little bandwidth or all the bandwidth you have.  The bad thing about NX is that the protocol isn't standard across all NX solutions.  Mixing an NX client from NoMachine with an NX server from x2go doesn't work (or vice versa).
[/LIST]

---

### Post by kotgc on 2023-12-21
Well done on 1/3rd the cost of Internet, any hints how to do that?
I used Remote Desktop before with VNC server and Remmina client, so it does work. The issue now is my ISP uses a CGNAT, so I've created a VPN/Tunnel with TailScale which is connected.
My remote viewer is usually a laptop, but for now I'm testing with a mobile and yes, it's too small but serves the testing purpose.

I ran this test command:
```

$ sudo apt install netcat-openbsd && nc -vv 1.1.1.1 80
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
netcat-openbsd is already the newest version (1.218-4ubuntu1).
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
Connection to 1.1.1.1 80 port [tcp/http] succeeded!

```
5900 does not connect, so perhaps port forward 5900 might help?
Happy to use whatever works, server VNC, client Remmina, NoMachine, RealVNC, RustDesk.

---

### Post by kotgc on 2023-12-22
[COLOR=#0C0D0E][FONT=-apple-system]Fixed using rdp, vnc is problematic with gnome.[/FONT][/COLOR]

---

