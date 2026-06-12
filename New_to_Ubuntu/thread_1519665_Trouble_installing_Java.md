---
title: "Trouble installing Java"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by Celestika6 on 2010-06-28
So I just upgraded to Lucid and when I tried to download Frostwire it told me that I didn't have Java. So I went to the Java website to download it and lo and behold it's a .bin file. I looked up how to install a .bin file and got some instructions, but I have no idea how to access a directory from my terminal.

I have the file (jre-6u20-linux-i586.bin) saved to my desktop. Can someone please give me very clear step-by-step instructions on how to install it? I'm a total technoklutz.

---

### Post by QIII on 2010-06-28
Don't do it that way.  There is no need to do that.

Activate the Lucid Partner repo and install via the repos (apt-get or Synaptic).

Update 20 is there.  If you install via the repo it will be automatically updated from the repo when the Java version is updated.

---

