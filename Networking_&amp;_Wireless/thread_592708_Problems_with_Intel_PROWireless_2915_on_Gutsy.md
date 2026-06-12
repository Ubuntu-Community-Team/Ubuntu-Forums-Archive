---
title: "Problems with Intel PRO/Wireless 2915 on Gutsy"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by jnholcomb on 2007-10-26
First, I'd Like to start out by saying I'm new to the forums. (and linux) wahzzup. 
Next, I'd like to say that although I've always loved the Idea of linux, but was always intimidated by abandoning my windows knowledge. whoah. new world.
And last, I upgraded to gutsy one day, using my Intel PRO/Wireless 2915 card that I installed in my ASUS z92 notebook. After my reboot, I was upset to find that network manager no longer detected/displayed/gave me wireless capability.:confused: I had to reinstall Feisty for a quick fix before school so I could use my wifi between classes.:mad:

anyway, It sounds like a driver problem, so I DL'd the drivers from Intels website, and I've honestly no idea how to install them. :lolflag: (big noob) I love the restriced driver manager and other features in gutsy so if someone could help me out that would be great, I'll check back in a while, hopefully someone can help. (I imagine so since this seems like a relatively easy problem to solve). 

Thanks!
-James

---

### Post by Lambert on 2007-10-27
you should not have to install any drivers for this device as it uses ipw2200 which comes with gutsy.

some suggestions.

1. search the forum for ipw2200 to see if you can find any others with posts on how they got this working in gutsy.
2. run the command 

```

sudo lshw -C network

```

Under the configuration line you should see something saying driver=ipw2200. If not then driver is not loaded.

Run this command

```

lsmod | grep ipw

```

this shows what modules are loaded. you should see ipw2200 listed. If not then try this.

```

sudo modprobe ipw2200

```

your driver should now be loaded and you should see your wireless interface.

after searching and trying this if you still have nothing, post back here with what you tried or found.

---

### Post by jnholcomb on 2007-10-28
Thanks, I'll try reinstalling gutsy tomorrow night, I think between your reply and another post I found searching under ipw2200 I can get it up. I didn't realize those ran from the same drivers.

---

