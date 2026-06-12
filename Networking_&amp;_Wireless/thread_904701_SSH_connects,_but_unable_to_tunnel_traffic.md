---
title: "SSH connects, but unable to tunnel traffic"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by tj.milligan on 2008-08-29
Summary:

SSH server running at home (server). WinXP and Ubuntu clients at work. Can establish ssh connection on both XP and Ubuntu clients, but only XP connection seems to "tunnel" -- e.g., firefox proxy, vnc connection. Need help sorting out why Ubuntu session doesn't "tunnel".

Detail:

I have OpenSSH server running on my WRT54GL [DD-WRT flashed linux-based] router at home. I used [win32] puttygen.exe to generate a public key for the server and a private key file (*.ppk) for client authentication (in place of a password). On the client side (work), I have a WinXP machine and I run Ubuntu Feisty in a VMware workstation virtual machine. I have Putty installed on my XP box [win32] AND my Ubuntu vm [apt-get install putty], and each machine has a local copy of the .ppk file needed for authentication.

Now here's where I'm stuck: Both my WinXP and Ubuntu clients are able to successfully connect via putty to the router (I get a # prompt). However, I can only seem to "use" the tunneled connection in Windows.

Example:

In WinXP, I open my ssh connection via putty (see putty config below). I confirm a ssh connection is made since putty logs me into a # promt at my router and I can type unix commands. At this point I can: 
a) Supply proxy info to Firefox and connect through proxy via ssh (Options > Advanced > Network > Manual Proxy config > SOCKS host: localhost, Port 3060).
b) Connect to VNC server over ssh (VNC server location: localhost:0).

However, In Ubuntu, I open my ssh connection via putty (see putty config below). I confirm a ssh connection is made since putty logs me into a # promt at my router and I can type unix commands. At this point I can't do either of the above. :confused:

Putty config (win32 & linux clients):

host: [me].dyndns.org:443
tunnel: Dynamic on port 3060
tunnel: Local on port 5900 at destination 192.168.1.[vnc-server-ip]:5900
(no password needed since .ppk file is used to authenticate)

[Able to provide more detailed information as needed -- Thanks in advance!]

---

### Post by tj.milligan on 2008-09-02
> **tj.milligan said:**
> Summary:

SSH server running at home (server). WinXP and Ubuntu clients at work. Can establish ssh connection on both XP and Ubuntu clients, but only XP connection seems to "tunnel" -- e.g., firefox proxy, vnc connection. Need help sorting out why Ubuntu session doesn't "tunnel".

"Fixed" by using *nix cli openssh client ("ssh") instead of the *nix Putty client. Never figured out why the Putty connection wouldn't tunnel. Hmph!

**Guide to Convert Putty private and public keys to OpenSSH format for use in *nix based environments**

*This guide assumes you have a [win32] puttygen created private key (*.ppk), and that you have an OpenSSH server, accessible over the internet via a dyndns domain at remote port 443. The example uses the default Puttygen encryption values (rsa 1024-bit), no passphrase.*

First, I had to use win32 puttygen to load the existing private key (*.ppk) file and then choose Conversions > Export OpenSSH key. Rename that to "id_rsa" and drop in *nix client ~/.ssh directory. This is the private key -- Halfway done!

Next, create another plaintext file in the client ~/.ssh directory named "id_rsa.pub" and type
```
ssh-rsa PUBLIC_KEY_HERE COMMENT
```
making sure word-wrap is turned OFF. Open the private key *.ppk file in a text editor and replace the text "PUBLIC_KEY_HERE" with the public key. Additionally, replace the text "COMMENT" with the text that follows "Comment: " in the *.ppk file. Save, making sure you have a 1-line file with no carriage return at the end. The public key is now ready.

Finally,
```
*$* chmod 700 id_rsa
```

You can leave your public key file (id_rsa.pub) with default 644 permissions, or change it to 700 as well -- your choice.

Here's the command I use to establish an ssh tunnel to my home ssh server, for use as a secure firefox proxy :)

```
*$* ssh -2 -D 3060 -p 443 [ssh-user]@[me].dyndns.org
```

In firefox, go to Edit (or Tools) > Preferences. Advanced > Network > Settings. Manual proxy configuration > SOCKS Host: localhost, Port 3060. Then "OK" and "Close" to confirm. Before you restart firefox, type about:config into the address bar and change network.proxy.socks_remote_dns to true. Restart firefox and you have secure ssh tunneled browsing!

This can be extended to secure VNC connections and more.

---

