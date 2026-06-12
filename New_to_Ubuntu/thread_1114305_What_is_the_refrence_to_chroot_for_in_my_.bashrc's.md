---
title: "What is the refrence to chroot for in my .bashrc's $PATH"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by hovzio on 2009-04-02
Hi, I was wondering what this reference to chroot in my path is for is for?

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;34m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```

A few lines above this it sets a variable if there is a readable /etc/debian_chroot file. (Which I do not have.) Is the bellow then later passed on to the prompt??


```
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

```


I have vague knowledge what a chroot jail is and does (In theory, haven't set one up yet) but I really don't get the jist of this. Is it like, If there is some type of chrooted programs setup, include these in my path??  Sorry if that sounds garbled but thats all I could come up with. When I echo my path there is no mention of chroot. I googled and didn't find much, did find a bunch of cool stuff, using command substition within prompt and doing some rather exotic things in terms prompt.. but nothing refering to this. Can I remove this from my $PATH? Thank you;)

---

### Post by hovzio on 2009-04-03
Oh I hate doing this...  *BUMP*.

---

### Post by unutbu on 2009-04-03
You can use the dchroot or schroot package to execute commands in a chroot environment. As part of the setup you can put a name in /etc/debian_chroot. Then, when you chroot (change root), your prompt will indicate what chroot environment you are in.

See [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

---

### Post by hovzio on 2009-04-03
Thank you unutbu. :) Sounds plausible. I guess the reason why I was asking was I'm writing a bashrc from scratch and was wondering if I had to set up the prompt in a similar manner. From what I can tell I have no plans for dchrooting so I assume I can leave it out. No reason specifically for writing a bashrc, I'm just experimenting. Thanks again :)

---

