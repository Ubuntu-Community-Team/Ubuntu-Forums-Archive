---
title: "SSH help"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Guffmeister on 2010-08-11
Hi, this should hopefully be an easy problem to solve, but I haven't a clue what's going on.

I'm SSHing into my work computer running Ubuntu 10.04 from home using Ubuntu 8.04 LTS. This is fine, and I can connect no problems. If I run Matlab, then it opens fine on the work comp, and I get the GUI forwarded to my computer. However, if I open firefox, it just opens the firefox version on my computer, which is irritating because there are some website tabs on my work computer that I need to see and I can't remember what they are called. Any reason why this is happening and any clues how to fix it? At work I use firefox all the time to email files across from one computer to another, and I've never had a problem, but now I'm home I can't seem to open it.

Weird.

Any help is appreciated! Thanks!

---

### Post by Drenriza on 2010-08-11
Is it even possible to open Firefox over a ssh connection?

My mind says: No
My Gut  says: Dunno

Edit.
Aparently it is possible
[http://wiki.freaks-unidos.net/weblogs/azul/firefox-ssh-tunnel](http://wiki.freaks-unidos.net/weblogs/azul/firefox-ssh-tunnel)
[http://www.theopensourcerer.com/2007/11/15/remote-firefox-over-xssh/](http://www.theopensourcerer.com/2007/11/15/remote-firefox-over-xssh/)
[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025) (howto guide from ubuntu forums)

---

### Post by spillage2 on 2010-08-11
yes you can open firefox over ssh but you will only see the page on the server side. you would be best running vnc through your ssh connection..please dont ask how as I am trying to resolve this myself.

---

### Post by Sunseeker.ch on 2010-08-11
I can't believe that. Can you explain in detail, what you're doing?
# user@home: ssh -X user@work-computer
# user@work:  firefox

something like that?

---

### Post by bodhi.zazen on 2010-08-11
firefox is an exception to the rule on X forwarding over ssh.

You need to use the --no-remote option

```
ssh -X user@server

server:# firefox --no-remote
```

 This is documented here;

[http://kb.mozillazine.org/Command_line_arguments](http://kb.mozillazine.org/Command_line_arguments)

Although the language is obscure, lol

---

### Post by Sunseeker.ch on 2010-08-11
I don't see the explanation for this effect on the mentioned page. But the effect itself is intresting.

Start a local firefox => remote started firefox will start a second instance of the local one.
Start a remote firefox => local started firefox will start a second instance of the remote one.

---

### Post by bodhi.zazen on 2010-08-11
> **Sunseeker.ch said:**
> I don't see the explanation for this effect on the mentioned page. But the effect itself is intresting.

Start a local firefox => remote started firefox will start a second instance of the local one.
Start a remote firefox => local started firefox will start a second instance of the remote one.

Exactly, the explanation is poor.

If you do NOT use the --no-remote, firefox starts on your local computer, even though you ran the command in ssh on the server 9at least last time I checked).

IMO, if you are going run firefox over ssh you are better off using a tunnel.

[Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html")

---

### Post by lovinglinux on 2010-08-11
> **Sunseeker.ch said:**
> I don't see the explanation for this effect on the mentioned page. But the effect itself is intresting.

Start a local firefox => remote started firefox will start a second instance of the local one.
Start a remote firefox => local started firefox will start a second instance of the remote one.

Without the -no-remote option Firefox opens a new window of the version currently running. If you started the local version first, this is the one which will launch another window and vice versa.

On a side note, you could sync tabs, bookmarks, passwords, history and settings between machines, with [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/"). If you need to keep data separate, then create a work profile at home and install Firefox Sync on it. To start the profile manager:

```
firefox -P
```

---

### Post by Guffmeister on 2010-08-11
Wow, thanks for all your help.

I often use SSH to connect to other work computers on the network from my main computer to run multiple simulations. I can load up firefox on these computers using the usual command in the terminal window once connected with no problems. 

In fact, I just tried connecting to a different computer to my main one, and ran firefox and it was absolutely fine, and I got the firefox from the other computer forwarded to my home computer.

Now, my user name on my home computer and main work computer are the same, but I have a different one for the other computers on the network...could this be the root of the problem perhaps? Either that, or is there some way that the firefox has been set up on the network computers differently so that it can be forwarded through SSH? I'm a bit out of my depth...I might have to email the linux techies at work because they set up the system.

Thanks for your help.

---

### Post by bodhi.zazen on 2010-08-11
> **Guffmeister said:**
> Wow, thanks for all your help.

I often use SSH to connect to other work computers on the network from my main computer to run multiple simulations. I can load up firefox on these computers using the usual command in the terminal window once connected with no problems. 

In fact, I just tried connecting to a different computer to my main one, and ran firefox and it was absolutely fine, and I got the firefox from the other computer forwarded to my home computer.

Now, my user name on my home computer and main work computer are the same, but I have a different one for the other computers on the network...could this be the root of the problem perhaps? Either that, or is there some way that the firefox has been set up on the network computers differently so that it can be forwarded through SSH? I'm a bit out of my depth...I might have to email the linux techies at work because they set up the system.

Thanks for your help.

IMO you are better off tunneling over ssh rather then forwarding firefox.

See my last post :

[Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html")

---

