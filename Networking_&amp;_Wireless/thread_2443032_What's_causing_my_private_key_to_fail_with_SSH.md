---
title: "What's causing my private key to fail with SSH?"
date: 2020-05-10
forum: Networking &amp; Wireless
---

### Post by Paddy Landau on 2020-05-10
**Background**

I access SSH in my GoDaddy's account using [FONT=lucida console]ssh[/FONT] and a public-private key pair. This has been working flawlessly for years. A few days ago, this stopped working (nothing changed on my end), and SSH ignores my private key, asking instead for the login password. GoDaddy's support team is adamant that the error lies on my side. (I'm not the only person having this problem with GoDaddy.) So, I'm trying to figure out where the error lies.

**Setup**

There is a public key on GoDaddy's server, in [FONT=lucida console]~/.ssh[/FONT]. I know that permissions are important, so here are the permissions of my home folder on GoDaddy's server:
```
drwx--x--x
```
Here are the permissions of [FONT=lucida console]~/.ssh[/FONT]:
```
drwx------ .ssh
```
And its contents:
```
-rw-r--r-- authorized_keys
-rw-r--r-- id_rsa_godaddy_paddy.pub
```
These permissions were set by GoDaddy's automated system.

On my side (the client), the permissions are the similar:
```
drwx------ /home/paddy
```
Here are the permissions of [FONT=lucida console]~/.ssh[/FONT]:
```
drwx------ .ssh
```
And its contents:
```
-rw------- config
-r-------- id_rsa_godaddy_paddy
-rw------- known_hosts
```


**Running ssh**

I run the following command (the items in curly brackets are redacted for security):
```
ssh -vvv -l *{username}* -i ~/.ssh/id_rsa_godaddy_paddy *{host.com}*
```
When this runs, the server rejects the private key (I can tell this by running PuTTY on Windows, but that gives me no other information), and prompts for my password instead.

I've been over the output from [FONT=lucida console]ssh[/FONT], but unfortunately I cannot find where the error is happening (I'm not clever with SSH). Can you help, please? The output is attached in file [FONT=lucida console]ssh.txt[/FONT].

Thank you

**EDIT:** I have checked [FONT=lucida console]/etc/ssh/ssh_config[/FONT] on the server side, and it contains neither [FONT=lucida console]AuthorizedKeysFile[/FONT] nor [FONT=lucida console]PubkeyAuthentication[/FONT], which means that the defaults are used.

---

### Post by TheFu on 2020-05-11
My ssh troubleshooting page: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

```
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug2: **we did not send a packet, disable method**
debug3: authmethod_lookup password
```

Looks like there is a problem with your ssh pub/priv key.  I'd just recreate one, this time using 
```
$ ssh-keygen -t ed25519
```
So the key is more secure than RSA.
Also, looks like your local ~/.ssh/config file has some settings for this specific server.  Check that those don't conflict. In the ~/.ssh/ all files should be 600, except public keys and known_hosts files. The config and all private keys (if any) need to be 600. There's usually little reason for a remote hosted system to have any private keys or a config file, so check your local workstation for permissions problems.

---

### Post by Paddy Landau on 2020-05-11
Thank you, @TheFu. Unfortunately, this hasn't solved the problem.

Yesterday, I had created keys with a password, so that I could tell whether or not SSH was even trying to access the key. When I try to connect, I get the following:
```
Enter passphrase for key '/home/paddy/.ssh/id_rsa_godaddy_paddy':
```
I enter the private key's password. If I use the incorrect password, it complains, so I know that it's getting the right key.
Having entered the password and accepted it, it nevertheless asks for the host's password:
```
{user}@{host}'s password:
```
That allows me to connect.

So, I can connect; I just can't use the key pair to do so.

Also, I have ensured that the client has the private key, while the server has the public key, and not vice-versa.

On the server side, [FONT=lucida console]~/.ssh/authorized_keys[/FONT] is identical to [FONT=lucida console]~/.ssh/id_rsa_godaddy_paddy.pub[/FONT].

Diagnoses:

[LIST]
[*]It looks as though GoDaddy doesn't support Ed25519. So, I've had to stick with RSA. I've tried both 2,048 and 4,096 bits.
[*]My [FONT=lucida console]~/.ssh/config[/FONT] contains the following for this particular server. (It contains another entry, but that's for a different account and host, which has the same problem, also on GoDaddy.)
```
Host gdy
   HostName    [I]{redacted}
[/I]   User        [I]{redacted}
[/I]   IdentityFile    ~/.ssh/id_rsa_godaddy_paddy
```
[*]I have tried accessing the server without the [FONT=lucida console]config[/FONT] file, using the following, with identical results.
[*]```
ssh -l {username} -i  ~/.ssh/id_rsa_godaddy_paddy {host]
```
[*]I have thoroughly checked permissions of [FONT=lucida console].ssh[/FONT] and its contents on both the client (my machine) and server (GoDaddy's machine). They are all 700 for [FONT=lucida console].ssh[/FONT] and 600 for its contents.
[*]There's no file [FONT=lucida console]~/.ssh/config[/FONT] on the server, although I had tried one earlier.
[/LIST]
Using your troubleshooting guide:

[LIST=1]
[*][FONT=lucida console]service ssh status[/FONT] — I don't have access to this on GoDaddy. On my machine, it returns "Unit ssh.service could not be found."
[FONT=lucida console]dpkg-query --list 'openssh*'[/FONT] — on my machine, this returns both [FONT=lucida console]openssh-client[/FONT] and [FONT=lucida console]openssh-server[/FONT]. It doesn't work on GoDaddy as it's not Debian.
[*][FONT=lucida console]ssh -vvv {username}@{host}[/FONT] — Already done, as per my OP.
[*][FONT=lucida console]lsof[/FONT] — I don't have authorisation on the server side, and I have no idea how to interpret the output on mine. However, as connection is possible (using a password and not the private key), am I correct that this isn't the problem?
[*][FONT=lucida console]ping {IP}[/FONT] — Works from both server and client.
[*][FONT=&amp]ping {host}[/FONT] — Works from both server and client.
[*]All file and folder permissions are correct, both server and client.
[*][FONT=lucida console]ssh -l {user} -i id_rsa_godaddy_paddy localhost[/FONT] — After copying the private key to the server, this connects, but it totally ignores the private key and just asks for the host's password.
[*]I can't test from the LAN, but if I enter the same command as from the client, it's the same result as step 7.
[*]As with step 8, I can't do this.
[*]As with step 8, I can't do this.
[/LIST]
GoDaddy's support has checked that my IP address hasn't been blocked. I've also tried accessing this via Windows using PuTTY, and via a different internet connection.

I have no clue how to proceed. I've spent hours on this in the past couple of days, and it's driving me crazy.

---

### Post by TheFu on 2020-05-11
Perhaps search for help on the OS forums for the server side? Do they run CentOS? Which version?  

When you push the public key up, are you using **ssh-copy-id**?

---

### Post by Paddy Landau on 2020-05-12
@TheFu, thank you for the time you've given.

It turns out that there must have been a problem with GoDaddy after all, because — hallelujah — it's working today!

So, the problem didn't lie on my end after all.

(I'm a bit cross with GoDaddy for having misled me.)

Today's experimentation has confirmed that GoDaddy doesn't support Ed25519, but it does support 4,096-bit RSA.

Sorry to have wasted your time. At least I learned a number of things along the way.

By the way, in case you're interested, answers to your questions:

I don't know what version of Linux GoDaddy uses. If I enter [FONT=lucida console]uname --all[/FONT], the following is returned:
```
Linux *{host}* 2.6.32-954.3.5.lve1.4.76.el6.x86_64 #1 SMP Mon Dec 23 07:33:14 EST 2019 x86_64 x86_64 x86_64 GNU/Linux
```

To create the key-pair, I either:

[LIST]
[*]Use GoDaddy's GUI, and download the private key to my computer; or
[*]Ceate the pair on my side using[FONT=lucida console] ssh-keygen[/FONT], and use copy-and-paste (using [FONT=lucida console]vi[/FONT]) to enter the key on GoDaddy's server.
[/LIST]
Both ways work.

Thanks again!

---

### Post by TheFu on 2020-05-12
2.6.3!!!!!  Fire them!  That is certainly only supported for embedded devices.  Looks like a CentOS 6 version.

BTW, I have GoDaddy as a registrar, but do not use them for DNS or hosting of any sort.  I renew domains every 10 yrs with a coupon. The hassles to switch registrars have never been sufficient against the 10 minutes needed to renew.

---

### Post by Paddy Landau on 2020-05-17
> **TheFu said:**
> 2.6.3!!!!!  Fire them!
Which host do you use, may I ask?

---

