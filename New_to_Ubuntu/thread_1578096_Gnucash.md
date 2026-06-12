---
title: "Gnucash??"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by k33bz on 2010-09-19
Does anyone know if you can use gnucash on a remote server?

If not does anyone know a financial application that can be run from a remote server?

---

### Post by Sef on 2010-09-19
I would suggest checking the [GNUcash]("http://www.gnucash.org/") website.

---

### Post by k33bz on 2010-09-19
> **Sef said:**
> I would suggest checking the [GNUcash]("http://www.gnucash.org/") website.

Actually that is what I been doing while waiting on a reply. Even looking through their wiki page. I am seeing that is possible, but as of yet not found out how to achieve this.

---

### Post by bodhi.zazen on 2010-09-19
ssh -X ?

You can forward graphical application over X, if you use Windows as a client, you will need putty and Xming.

You can transfer files over ssh as well (scp). The windows client is graphical and is called winscp

If that does not work, what is it you are needing ?

---

### Post by k33bz on 2010-09-20
> **bodhi.zazen said:**
> ssh -X ?

You can forward graphical application over X, if you use Windows as a client, you will need putty and Xming.

You can transfer files over ssh as well (scp). The windows client is graphical and is called winscp

If that does not work, what is it you are needing ?

ok, so doing that, I would need to install gnucash on the server? Correct?

O wow, I hope not, doing so is wanting to install gnome-desktop as well, and that is something I do not want on my server, I want it to stay command line.

Going to see if I cant use source.

---

### Post by bodhi.zazen on 2010-09-20
> **k33bz said:**
> ok, so doing that, I would need to install gnucash on the server? Correct?

O wow, I hope not, doing so is wanting to install gnome-desktop as well, and that is something I do not want on my server, I want it to stay command line.

Well, gnucash is an X application, so you would need to install X.

gnome-desktop is , IMO, overkill, too many dependencies listed. You might have better luck with Debian or Slackware or Gentoo (Less dependencies).

I would intsall gnucash + openssh on a dedicated Desktop . Just be sure to secure ssh (keys, no password, etc).

---

### Post by k33bz on 2010-09-20
> **bodhi.zazen said:**
> Well, gnucash is an X application, so you would need to install X.

gnome-desktop is , IMO, overkill, too many dependencies listed. You might have better luck with Debian or Slackware or Gentoo (Less dependencies).

I would intsall gnucash + openssh on a dedicated Desktop . Just be sure to secure ssh (keys, no password, etc).

went through alot, started having dependecy hell by building from source. GLIB was giving me problems. I may use Gnucash just on my laptop. 

Grisbi seems to let me run from my server with out the extra steps. So I will use Grisbi on the server itself.

No worries, I will be securing ssh as described in a post you made in another thread of mine.

You dont by any chance know a way I can stream Audacious from my server to client machine do ya?

---

### Post by bodhi.zazen on 2010-09-20
Icecast ?

[http://www.korokithakis.net/tutorials/icecast](http://www.korokithakis.net/tutorials/icecast)

---

### Post by k33bz on 2010-09-20
I will have to check that out later, having problem 

```
emacs: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime

```

I am thinking this happened when I tried to install glib 2.9 from their ftp site. Working on getting rid of error.

ok thats fixed, good thing I still had the tarball.

---

### Post by k33bz on 2010-09-20
> **bodhi.zazen said:**
> Well, gnucash is an X application, so you would need to install X.

gnome-desktop is , IMO, overkill, too many dependencies listed. You might have better luck with Debian or Slackware or Gentoo (Less dependencies).

I would intsall gnucash + openssh on a dedicated Desktop . Just be sure to secure ssh (keys, no password, etc).

on the tutorial you ahve on your site [http://bodhizazen.net/Tutorials/ssh/]("http://bodhizazen.net/Tutorials/ssh/") Do I generate both keys on the client (rsa & dsa)? Then transfer them over to the server? Just want to make sure I am reading it right.

---

### Post by bodhi.zazen on 2010-09-20
> **k33bz said:**
> on the tutorial you ahve on your site [http://bodhizazen.net/Tutorials/ssh/](http://bodhizazen.net/Tutorials/ssh/) Do I generate both keys on the client (rsa & dsa)? Then transfer them over to the server? Just want to make sure I am reading it right.

yes

generate them on the client, then use ssh-copy-id to transfer to the server

Then log into the server via the key and if that works, disable password login.

---

### Post by k33bz on 2010-09-20
Ok, I just got through doing that, I followed your tutorial, however I came across a problem with the public keys:
```
keebler@mobile:~$ ssh keebler@192.168.1.4
Ubuntu 10.04.1 LTS \n \l

Permission denied (publickey).

```
What can I do to fix this, and where did I go wrong. 

(I know it is not a lost cause since my file server is right in front of me, so I could manually log into my server and change the config files again to disable keys)

Sorry, it was this tut I followed, it differs from yours a bit
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

it never asked for this ```
You should be prompted for the passphrase for your key: 
```

Working on the troubleshoot that is at bottom. Was this to be done on client or server?
```
keebler@mobile:~$ sudo chmod 700 ~/.ssh
keebler@mobile:~$ sudo chmod 600 ~/.ssh/authorized_keys
chmod: cannot access `/home/keebler/.ssh/authorized_keys': No such file or directory
keebler@mobile:~$ 
```

```
keebler@mobile:~$ ls ~/.ssh
id_rsa  id_rsa.pub  known_hosts
keebler@mobile:~$ 
```

---

### Post by k33bz on 2010-09-20
> **k33bz said:**
> Ok, I just got through doing that, I followed your tutorial, however I came across a problem with the public keys:
```
keebler@mobile:~$ ssh keebler@192.168.1.4
Ubuntu 10.04.1 LTS \n \l

Permission denied (publickey).

```
What can I do to fix this, and where did I go wrong. 

(I know it is not a lost cause since my file server is right in front of me, so I could manually log into my server and change the config files again to disable keys)

Sorry, it was this tut I followed, it differs from yours a bit
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

it never asked for this ```
You should be prompted for the passphrase for your key: 
```

Working on the troubleshoot that is at bottom. Was this to be done on client or server?
```
keebler@mobile:~$ sudo chmod 700 ~/.ssh
keebler@mobile:~$ sudo chmod 600 ~/.ssh/authorized_keys
chmod: cannot access `/home/keebler/.ssh/authorized_keys': No such file or directory
keebler@mobile:~$ 
```

```
keebler@mobile:~$ ls ~/.ssh
id_rsa  id_rsa.pub  known_hosts
keebler@mobile:~$ 
```

ok, nvm, I needed to chmod on the server itself.

Question arises though. My computer is not the only one that needs access to the server. There is one other one, how do I go about getting her keys? Do I generate new keys, or do I transfer keys to her, and how would I go about it.

---

### Post by perspectoff on 2010-09-20
My remote access tips are at:

[http://kubuntuguide.org/Lucid#Remote_Access](http://kubuntuguide.org/Lucid#Remote_Access) (Kubuntuguide)

and

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Remote_Access) (Ubuntuguide)

also see more tips at:

[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

I routinely provide access to multiple users with SSH. I generally recommend that each user have their own public/private keypair, but you can share the private key, if you choose. The keypair is linked to the login ID, so if you share the SSH keypair, you must share the login ID as well.

If you want the second user to have her own login ID, you must generate a new keypair for her.

---

### Post by k33bz on 2010-09-20
> **perspectoff said:**
> My remote access tips are at:

[http://kubuntuguide.org/Lucid#Remote_Access](http://kubuntuguide.org/Lucid#Remote_Access) (Kubuntuguide)

and

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Remote_Access) (Ubuntuguide)

also see more tips at:

[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

I routinely provide access to multiple users with SSH. I generally recommend that each user have their own public/private keypair, but you can share the private key, if you choose. The keypair is linked to the login ID, so if you share the SSH keypair, you must share the login ID as well.

If you want the second user to have her own login ID, you must generate a new keypair for her.

ok, she has her own login on the server, so do I temporary disable keys, then generate her keys on her laptop then transfer over like I have done before, or is there another way to do so with out disabling keys?

---

### Post by bodhi.zazen on 2010-09-20
> **k33bz said:**
> ok, nvm, I needed to chmod on the server itself.

Question arises though. My computer is not the only one that needs access to the server. There is one other one, how do I go about getting her keys? Do I generate new keys, or do I transfer keys to her, and how would I go about it.

You can generate one key per client or many people keep keys on a flash drive.

the key is what you need. key.pub goes on the server (although I keep both on a flash drive, encrypt the flash drive if (paranoid).

---

### Post by k33bz on 2010-09-20
> **bodhi.zazen said:**
> You can generate one key per client or many people keep keys on a flash drive.

the key is what you need. key.pub goes on the server (although I keep both on a flash drive, encrypt the flash drive if (paranoid).

Thank you all so much. :)

---

### Post by k33bz on 2010-09-20
I did not see this line in the config file

```
AllowUsers goodboy1 goodgirl2 # White list by username
DenyUsers badboy1 badgirl2 # Black list by username
AllowGroups sshlogin # White list by groups
```

Do I just add the lines? Would like to whitelist user names if possible. Server is running 10.04 if that makes a difference.

Also wanted to know what feature of security does this add
```
Banner /etc/issue.net # I change this to /etc/ssh.login
```

---

### Post by bodhi.zazen on 2010-09-20
You can use allow/deny user/group, just use the proper names.

Deny user is on little use unless you wish to specifically deny a user on your system.

a banner is not security, it is a message users will see when they try to connect.

---

### Post by k33bz on 2010-09-20
> **bodhi.zazen said:**
> You can use allow/deny user/group, just use the proper names.

Deny user is on little use unless you wish to specifically deny a user on your system.

a banner is not security, it is a message users will see when they try to connect.

Ya but as I was asking, I dont see AllowUsers anywhere in the config file. So do I add a line that says AllowUsers and make it as such
```
AllowUsers keebler vronpen
```
 
and where should I add the line AllowUsers?

---

### Post by perspectoff on 2010-09-20
> **bodhi.zazen said:**
> You can generate one key per client or many people keep keys on a flash drive.

the key is what you need. key.pub goes on the server (although I keep both on a flash drive, encrypt the flash drive if (paranoid).

Heh. Heh. That's exactly the way I do it, for exactly the same paranoid reason.

But he can also do the keygen and transfer the key over the Internet (using ssh-copy-id), as he was asking. Only problem is, I find that the minute (literally) that my openSSH is unprotected, I have a ton of port scanning and brute-force password cracking attempts for the SSH port. God forbid if I don't have at least a strong password on the OpenSSH connection initially! A side-result of brute-force password cracking attempts is that the server loses time responding to them. (In this way it is somewhat similar to a Denial of Service attack).

I indeed have used ssh-copy-id over a password-protected SSH connection (when the user isn't in physical proximity), but I sure do it quickly and then turn off the password authentication (in the SSH config file) immediately after transferring the key. 

For the most part, though, I have gone to the flash drive method for transmitting keypair data, as well.

Just as a plug, I think knockd is a great little security device for people who want port security. 

I don't use port 22 for my SSH connections, anymore, but have changed it (by editing the ssh config file on the server) to a non-standard port.

Using knockd, I can hide that port and open it only when the correct sequence of port requests is made from the Internet. This keeps my SSH port always hidden. Sure, there's a miniscule additional negotation time built-in, but for the security it affords, it's worth it. Further, hiding the port almost completely halts Denial of Service attacks. No attacker program has the patience to probe ports in varying sequences in order to try to open a single non-standard port on which it can then attempt a brute force attack for an unknown type of server.

Too many wolves at the Internet door these days. Best security practices are crucial.

---

