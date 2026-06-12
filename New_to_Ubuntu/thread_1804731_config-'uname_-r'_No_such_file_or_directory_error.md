---
title: "config-'uname -r': No such file or directory error"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by u bun tu on 2011-07-15
When I use the command:

sudo cp boot/config-'uname -r' ./.config

I get the following error:

cp: cannot stat 'boot/config-uname -r': No such file or directory

When I use the command:

uname -r

The output is:
2.6.38-1208-omap4

The ls -l command in the boot directory displays the file:
config-2.6.38-1208-omap4

The command below works:
sudo cp boot/config-2.6.38-1208-omap4 ./.config

It doesn't read the quotations, 'uname -r' isn't being seen.

Is there something that I am doing wrong? Also, is there a difference between using ./.config versus .config?

Note: The commands are being done in the /usr/src/linux directory

If anyone can help, that would be great!

---

### Post by mcduck on 2011-07-15
Your problem is that you are using single quotes around the "uname -r", while you should be using backticks instead.

```
sudo cp boot/config-`uname -r` ./.config
```

(backticks make the shell execute the command inside them, and then place the result in place of that command. So that allows you to execute a command inside another command)

---

### Post by nothingspecial on 2011-07-15
Actually, these days you should use $(command)

```
sudo cp /boot/config-$(uname -r) ./.config
```

for command substitution.

---

### Post by u bun tu on 2011-07-15
Thanks everyone!

Both methods work, the `backticks` and the $(command)!

It was driving me crazy!

---

