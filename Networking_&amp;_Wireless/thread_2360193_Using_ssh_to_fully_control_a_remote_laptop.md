---
title: "Using ssh to fully control a remote laptop"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by saegerei on 2017-05-02
My machine is a Ubuntu 16.4 laptop and so is the remote one. While I'm logged-in via ssh and VPN the remote machine is unattended. It is at runlevel 5 with an auto-login user.

Problem: Suspend mode starts after 20 minutes. While I'm trying to accomplish some maintanance tasks.

Q1: How can I turn off suspend mode? Stopping service acpi has no effect. Wake-up via LAN is not an option since the machine is connected to its router via WLAN.

Q2: Can I start _any_ X-Application on the running desktop? Or how can I start some VNC server giving me access to the already running desktop?

---

### Post by SeijiSensei on 2017-05-02
For question two, the answer is yes.  Connect with "[FONT=Lucida Console]ssh -X[/FONT]" and it will set up an X tunnel back to your client.  Then if you run a graphical program from the terminal prompt, the output will appear on the client's screen.  Run the program in the background ("firefox &") so you can continue the terminal session.

---

### Post by ian-weisser on 2017-05-02
Question #1: If using Gnome or Unity, it's a gsetting in Power Manager.
See [https://askubuntu.com/questions/576525/is-there-any-way-to-make-ubuntu-not-to-suspend-while-a-download-in-progress](https://askubuntu.com/questions/576525/is-there-any-way-to-make-ubuntu-not-to-suspend-while-a-download-in-progress)

---

### Post by saegerei on 2017-05-02
Thank you both.

> **SeijiSensei said:**
> For question two, the answer is yes.  Connect with "[FONT=Lucida Console]ssh -X[/FONT]" and it will set up an X tunnel back to your client.  Then if you run a graphical program from the terminal prompt, the output will appear on the client's screen.  Run the program in the background ("firefox &") so you can continue the terminal session.
What happens with user data? They will go to my own home direcotry on the remote machine, right? Is there any chance to get something like a VNC session for the already running X session when nobody sits in front of the remote machine? I am a sudoer. I'd like to write user data (settings) on behalf of the other user that is already logged in.

[QUOTE=ian-weisser]Question #1: If using Gnome or Unity, it's a gsetting in Power Manager.[/QUOTE]
I'll test the KeepAwake.py script in the linked topic. However, I do not have access to the gsetting of the other user's running X session. I'll see if my gsettings can override the other user's gsettings.

---

### Post by SeijiSensei on 2017-05-02
> **saegerei said:**
> What happens with user data? They will go to my own home direcotry on the remote machine, right? Is there any chance to get something like a VNC session for the already running X session when nobody sits in front of the remote machine? I am a sudoer. I'd like to write user data (settings) on behalf of the other user that is already logged in.
I'm not sure I understand.  If you open a terminal on the remote machine, and you have sudo privileges, then you can write anything anywhere you want.

If you run 
```
ssh -X username@server
```
then you will be logged as "username" on the remote machine. As an ordinary user, anything you save will be stored in username's home directory, /home/username.  But if username has sudo privileges on the remote machine, then you can wreak any havoc you want on that machine.  You can use chown and chmod to change the ownership and permissions on files you create so they will belong to the proper user.

If you have sudo privileges, you can become another user like this:
```
sudo su phyllis
```
and you will have the same privileges you'd have if you logged in directly as phyllis.

If you use shared keys for authentication, you can put your public key in /home/phyllis/.ssh/authorized_keys and log in directly with
```
ssh -X phyllis@server
```

I haven't used VNC for a very long time.  Most of my time spent on remote machines happens at the command prompt.  I do run the occasional graphical application with "ssh -X" when I need to.

---

### Post by ian-weisser on 2017-05-02
> **saegerei said:**
> I'll test the KeepAwake.py script in the linked topic. However, I do not have access to the gsetting of the other user's running X session.

You don't need the whole script.
You only need the command within the script.
You can easily see that setting the opposite using a similar command bit will restore suspend when you are finished.
There are other ways, using dbus to talk to Power Manager, without wandering through gsettings. They are simpler...if you are already familiar with dbus.
You certainly should not need an X session running to do it either way, let alone somebody else's X session.

---

### Post by saegerei on 2017-05-03
Other people's Python scripts can be a nightmare. That one does not work for me although I adjusted a few variables. I could decypher the gsettings call that disables suspend mode. 
```
ssh -X me@remote
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
```
gsettings requires -X forwarding. 
Thank you both. Issue resolved.

---

### Post by saegerei on 2017-05-03
No, this does not work actually. Right now the connection is lost while editing a config file. I have to wait until someone comes home to turn on that machine again. Last resort: Reboot every 15 minutes.

P.S. When I run
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0

and 

gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 1800

on my own system, can I see in the system settings that it works. Doing the same from another log-in while I am logged in does not change anything.

---

### Post by saegerei on 2017-05-05
I think I found a way on my local machine. Let guest-byumgq be a temporary guest user on my local system on xterminal :1
```
[COLOR=#008000]me@localhost:~$[/COLOR] HOME=guest-byumgq sudo --user=guest-byumgq bash --login
[COLOR=#008000] guest-byumgq@localhost:~$[/COLOR] DISPLAY=:1 gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
[COLOR=#008000] guest-byumgq@localhost:~$[/COLOR] DISPLAY=:1 gsettings set org.gnome.Vino enabled true
```
disables sleep mode for the logged in user on xterm :1 and turns on the built-in VNC server "Vino".

---

