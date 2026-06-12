---
title: "How to allow non-root user to run ip netns exec"
date: 2015-10-20
forum: Networking &amp; Wireless
---

### Post by lambdafox on 2015-10-20
I found this suggestion on [unix.stachexchange.com]("http://unix.stackexchange.com/questions/229548/allow-regular-users-to-use-network-namespaces")

[TABLE="width: 660"]
[TR="class: comment"]
[TD][TABLE]
[TR]
[TD="class: comment-score"][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[QUOTE][/TD]
[TD="class: comment-text"]why dont you define Cmd_Alias CMD_NETNS = ip netns exec [regexp matching your namespace] su [regexp matching allowed used] -c [regexp matching allowed namespace command] in your sudoers file and then create a group in which you put your allowed users, and associate this group to this command alias. – [netmonk]("http://unix.stackexchange.com/users/128153/netmonk") [COLOR=#999999][Sep 14 at 11:50]("http://unix.stackexchange.com/questions/229548/allow-regular-users-to-use-network-namespaces#comment391648_229548")[/COLOR][/TD]
[/TR]
[/TABLE]

I am aware that Xubuntu Vivid has adopted policykit and has continuing support for sudo.  I do not exactly understand when to use which.  With that confusion in my mind, I am asking is this the proper way to do this in Vivid?

Thank you.

---

### Post by michi1983 on 2015-10-20
> **lambdafox said:**
> I found this suggestion on [unix.stachexchange.com]("http://unix.stackexchange.com/questions/229548/allow-regular-users-to-use-network-namespaces")
 I do not exactly understand when to use which.
Thank you.
What exactly do you mean? Sorry but I don't understand your question if there is one :-)

---

### Post by lambdafox on 2015-10-20
Currently running any command beginning ip netns exec somenamespace requires sudo or sudo su to make it work.

I would like to run, for example:

ip netns exec somenamespace firefox 

without requiring a root password.

I don't know if it matters, but I am the only user of my system.

Thank you.

---

### Post by michi1983 on 2015-10-20
oh okay. maybe you can find your information here:
[http://superuser.com/questions/636726/allow-users-of-a-certain-group-to-run-a-command-without-sudo](http://superuser.com/questions/636726/allow-users-of-a-certain-group-to-run-a-command-without-sudo)

---

### Post by lambdafox on 2015-10-20
looking at the link you provide, I think you indirectly answered my original question, which was whether modifying the sudoers file still works for this in Vivid, is that correct?

---

### Post by michi1983 on 2015-10-20
I think so, yea

---

