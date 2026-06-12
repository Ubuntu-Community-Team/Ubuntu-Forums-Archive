---
title: "Help running Vbox additions.."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by dorseye on 2009-01-25
I am having trouble getting vbox additions installed.
I have a host Windows Vista machine.
I have a guest Vbox Ubuntu Linux (Gutsy Gibbon)

[http://pastebin.com/m4240dceb](http://pastebin.com/m4240dceb)

I am trying to install the VboxAdditions to be able to adjust my resolution. As far as I can tell, I am in the current directory where the .run file exists, yet when I try to run it with ./ it doesn't seem to think the file is in the same directory. Can someone tell me what I'm doing wrong?

---

### Post by Procuro on 2009-01-25
Hi, try capitalizing the B in VBox to match the filename. Case sensitivity can be a pain especially with long files.

---

### Post by boof1988 on 2009-01-25
> **dorseye said:**
> I am having trouble getting vbox additions installed.
I have a host Windows Vista machine.
I have a guest Vbox Ubuntu Linux (Gutsy Gibbon)

[http://pastebin.com/m4240dceb](http://pastebin.com/m4240dceb)

I am trying to install the VboxAdditions to be able to adjust my resolution. As far as I can tell, I am in the current directory where the .run file exists, yet when I try to run it with ./ it doesn't seem to think the file is in the same directory. Can someone tell me what I'm doing wrong?

If you are in the same directory, do you still need the "./"?

I was in the same directory as the script and used:

```
sudo bash <ScriptName> # without the leading ./
```

and operation/compiling completed without error.

---

### Post by boof1988 on 2009-01-25
> **Procuro said:**
> Hi, try capitalizing the B in VBox to match the filename. Case sensitivity can be a pain especially with long files.

Or (if it's available) use <Tab>-completion.

---

### Post by dorseye on 2009-01-25
> **Procuro said:**
> Hi, try capitalizing the B in VBox to match the filename. Case sensitivity can be a pain especially with long files.

Argh -- this was the problem :/ A simple capitalization error.. Just proves you shouldn't do these things at 12:15 AM :) Thank you all!

---

