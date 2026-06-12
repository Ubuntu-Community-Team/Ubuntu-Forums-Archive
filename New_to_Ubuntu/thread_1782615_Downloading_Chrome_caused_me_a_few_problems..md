---
title: "Downloading Chrome caused me a few problems."
date: 2011-06-14
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-06-14
Hi all,

Like a fool, I attempted to download chrome directly from the internet. Nothing appeared in the internet menu and I now find that in the task bar there is now no shutdown menu in the top right hand side. At the present I am running Classic (no effects)

How can I -

1. Restore shutdown menu.

2. Completely purge whatever it was that I supposedly downloaded. The site I attempted the download from was I believe a genuine Google site.

I will be very grateful for any help,

Thank you.

---

### Post by wolfen69 on 2011-06-14
Right click the panel and go to "add to panel". You should see a shutdown thingy in there.

Search synaptic for chrome and *completely remove*.
then
```
sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by OldBoy44 on 2011-06-14
Thanks wolfen69,

Chrome does not show up in synaptic, 

Should I still run command?

I couldn't find the right menu in task bar options - I will keep looking.

Thanks,

---

### Post by OldBoy44 on 2011-06-14
I found the menu - but don't know how to get it in RHS.?

---

### Post by wolfen69 on 2011-06-14
> **aussiebean said:**
> I found the menu - but don't know how to get it in **RHS**.?

You mean right hand side? Just right click the icon and choose "move". Then drag it where you want.

---

### Post by OldBoy44 on 2011-06-14
Thanks again wolfen69,

I have successfully moved icon but now the user name has disappeared.

In the meantime I will enter the clean command.

Cheers, :)

---

