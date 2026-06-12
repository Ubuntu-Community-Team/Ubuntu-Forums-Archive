---
title: "How can I enable standard repositories with CLI"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by crjackson on 2009-05-26
I would like the terminal commands that will enable all of Ubuntu's included repositories (except proposed). I plan to put them in a bash script and have the script also install my default packages.

I already have the commands for medibuntu (external/restricted), I just need the rest.

Any help would be appreciated.

---

### Post by amingv on 2009-05-26
The only way I know of doing this via CLI would be editing sources.list through vim or nano (making a script to edit it would be too tedious, at least to my limited knowledge).

If you want to automate this task you could make a sources.list file with all the necessary repos enabled, have your script backup the old one and replace it with the new one (without much effort, you could even make it independent to the ubuntu version).

My $0.02.

---

### Post by crjackson on 2009-05-26
> **amingv said:**
> The only way I know of doing this via CLI would be editing sources.list through vim or nano (making a script to edit it would be too tedious, at least to my limited knowledge).

If you want to automate this task you could make a sources.list file with all the necessary repos enabled, have your script backup the old one and replace it with the new one (without much effort, you could even make it independent to the ubuntu version).

My $0.02.

It can be done. I read a post here and tried it out, but now I can't find the post. Thanks for the reply.

---

### Post by amingv on 2009-05-26
Well, I'll be darned. It looks like it can be done easily with sed:
[https://help.ubuntu.com/community/Repositories/CommandLine#Enabling%20Repositories%20with%20a%20(non-interactive)%20Script](https://help.ubuntu.com/community/Repositories/CommandLine#Enabling%20Repositories%20with%20a%20(non-interactive)%20Script)

Got to make some time and learn sed, I'm falling behind :(

---

### Post by crjackson on 2009-05-28
> **amingv said:**
> Well, I'll be darned. It looks like it can be done easily with sed:
[https://help.ubuntu.com/community/Repositories/CommandLine#Enabling%20Repositories%20with%20a%20(non-interactive)%20Script](https://help.ubuntu.com/community/Repositories/CommandLine#Enabling%20Repositories%20with%20a%20(non-interactive)%20Script)

Got to make some time and learn sed, I'm falling behind :(

Thanks for finding that page, I think the one below is what I'm looking for.

```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
```

The only problem is that this will also enable the proposed repository and I would like to exclude that one.

---

### Post by unutbu on 2009-05-28
Maybe do this:

```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
sudo sed -i -e 's/deb\(.*\)proposed/# deb\1proposed/g' /etc/apt/sources.list
```

---

### Post by crjackson on 2009-05-29
Okay, I'll try that this weekend. Thanks for the help...

---

