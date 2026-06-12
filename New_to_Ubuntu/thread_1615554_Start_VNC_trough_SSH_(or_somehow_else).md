---
title: "Start VNC trough SSH (or somehow else)"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Charlie Firpo on 2010-11-07
Hello all,
I ve been using Windows for years and now I finaly set up my first Ubuntu Box (10.10 Maverick) and I its awesome!
I now finaly understand why so many people are so enthusiastic about Linux/Ubuntu.
It is realy like I ve been riding the bus for years and now I got my own car...and a good one:P


But still there is a problem that relay gives me hedaches.

The problem is that when I try to acces the Ubuntu-machine from my win-pc (using real VNC on win, build in vino on Ubuntu), I have to type the root pw to accept the VNC-Connection. Now that is ofc not to cool because when I have to get the Ubuntumachine-Keyborad I do not need VNC.

Before you tell me to search (I really did search and found great solutions for other issues here:) heres what I found and what didn t work:

1) I can logon trough putty using ssh but when I try to start the vino-server with:
/usr/lib/vino/vino-server
I just cant start that "vino-server file"

2) I tried to start other vnc servers like tightvnc and vnc4server but no succes.

resume:
The network works. Ubuntu 10.10. Winxp PC with real VNC. I can logon trough ssh and vnc but when I restart the ubuntumachine (trough ssh) real VNC will not connect unless I enter the root pw trough the keyboard.


best regards

Charlie

---

### Post by SlugSlug on 2010-11-07
Have you had a look through vino-prefrences ?

I think there is an option to auto accept or somit,

---

### Post by HermanAB on 2010-11-07
Hmm, do yourself a favour and on Windows, install Cygwin with OpenSSL and OpenSSH.  Then open a Cygwin console:
$ ssh -X -C -c blowfish user@linuxmachine "gedit /etc/fstab"

or 
$ ssh -X -C -c blowfish user@linuxmachine gnome-panel

and go click happy.

If you already have SSH, then VNC is redundant.

---

### Post by CharlesA on 2010-11-07
+1 to Herman.

Forwarding X is really superior to VNC.

vino will only start is there is a user logged into the physical console, so I don't know if you can start it manually or not (but I doubt it)

---

### Post by Charlie Firpo on 2010-11-07
Hi there,
and Thanx for your replies!
The checkbox that a connection must be ackonwledged is unchekced. So I think it must work... but i doesnt :(

@ herman

Do I need to use cygwin or can also logon via putty?

When I type in:
$ ssh -X -C -c blowfish user@linuxmachine gnome-panel

Does this give me an acces "like VNC" by forwarding the panel?

And by "redundant" do you mean that the VNC features are covered by this method or is it only redundant if you are a mighty user that can do everthing trough the console?

I guess user is my username but what do use for "linuxmachine"? The IP?

---

### Post by CharlesA on 2010-11-07
By installing cygwin, you have an Xserver installed as well I believe. Using that command to forward the panel would make it almost like VNC, without the security risks.

You can also try to via Putty and something like XMing for the X server.

linuxmachine = ip address or hostname.

---

### Post by HermanAB on 2010-11-07
Howdy,

SSH can forward X function calls from the remote machine to a local X server.  So to run a graphical program remotely using SSH, you need to run an X server locally.  With Linux on the local machine that is not a problem.  For Windows, you need to install a X server.  The best one is Cygwin and then you don't need PuTTY either.

You could try to install Xming, but be sure to run it before you run PuTTY.

---

### Post by Charlie Firpo on 2010-11-07
Hi,
ok I am convinced that the best way to do it is Forwarding X.

So to make not knowing embarassing complete:

- Do frowarding X mean that you remotely start an application a forward the output/input to the machine you start it from?
- And if yes, does this mean I start the "gnome desktop application" so that I have full access to the desktop?

If thats what you were talking about it sounds really like a good idea.

But unfortunetely when I type in
ssh -X -C -c blowfish user@linuxmachine gnome-panel
on the shell (via putty) it tells me (after typing in the pw for user):
bash:gnome: command not found

I guess this goes depper than  I thought, so I d like to ask if you can sugest a good tutorial for this or (if its not to much effort) post a "click here, type this, instruction"

best regards

charlie

---

### Post by CharlesA on 2010-11-07
Try connecting first and then starting the panel.

---

### Post by Charlie Firpo on 2010-11-07
> **CharlesA said:**
> Try connecting first and then starting the panel.

I am connected because if wasn t I could not be able to type in commands?

Thats what I did

1) Start Putty on win pc

2) logon to linux pc via SSH (port 22)

3) loging in as a su

And there I typed in the command....guess that was wrong...?

---

### Post by CharlesA on 2010-11-07
You don't need to su.

Try running gedit and see what happens.

---

### Post by Charlie Firpo on 2010-11-07
okay when I do:
ssh -X -C -c blowfish user@linuxmachine gedit
I get:
(gedit:2174): Gtk-WARNING **: cannot open display:

---

### Post by CharlesA on 2010-11-07
If you are doing it from putty, you need to use something like XMing (download and install it) running to be able to forward X over SSH.

---

