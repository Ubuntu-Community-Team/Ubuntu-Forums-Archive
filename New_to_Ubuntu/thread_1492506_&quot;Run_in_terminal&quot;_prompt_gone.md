---
title: "&quot;Run in terminal&quot; prompt gone"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Nostigex on 2010-05-24
Usually when I click on a script, it gives me a box with the options of opening the file in gedit or running it in a terminal. For some reason that box has disappeared and now the file is automatically opened in gedit. Since I don't know how to run this particular script *from* the terminal (Get64bitFlash, which is not .sh), this is a big problem. Ideas?

---

### Post by anarchywolf46 on 2010-05-24
```
cd /<directory of Get64BitFlash>
chmod 755 Get64BitFlash
./Get64BitFlash
```Try that?

---

### Post by Nostigex on 2010-05-25
That didn't work, though I did get the script to run. It was originally on a storage partition (ext4) and I decided to try moving it to the home folder, upon which it was able to run. Does anyone know why it would be like this? Do I need to download scripts to the Filesystem whenever I want to run them?

---

### Post by anarchywolf46 on 2010-05-26
You should be able to run it on external storage, I decided to test it out to be sure and it worked just fine. It might be how the script was made that caused it to not work without being on the file system. That's just my guess though.

---

