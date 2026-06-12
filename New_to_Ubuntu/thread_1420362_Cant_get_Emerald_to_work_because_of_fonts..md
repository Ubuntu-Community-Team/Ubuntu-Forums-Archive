---
title: "Cant get Emerald to work because of fonts."
date: 2010-03-03
forum: New to Ubuntu
---

### Post by -spy on 2010-03-03
I have the themes showing up in Emerald, but nothing happens when i try to apply them.

Doing "emerald --replace" gets me this

"Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

I think this may have to do with me installing some font smoother a few weeks ago (the font looked terrible). Anyway to switch to default? I cant remember what I did exactly.

---

### Post by mcduck on 2010-03-03
Could you post the contents of your "~/.fonts.conf"-file here? (it's a hidden file inside your home director, press Ctrl-H  to make it visible in the file manager.)

Like your error message says, there's something wrong with the first line of that file.

---

### Post by -spy on 2010-03-03
> **mcduck said:**
> Could you post the contents of your "~/.fonts.conf"-file here? (it's a hidden file inside your home director, press Ctrl-H  to make it visible in the file manager.)

Like your error message says, there's something wrong with the first line of that file.

Not sure if this is what you wanted, but:

<?xml version=”1.0”?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>

---

### Post by mcduck on 2010-03-03
weird, since the XML declaration seems completely valid. Only thing I can see that might be wrong with it that all your quote marks are curled ones instead of straight quotes (” VS ").

---

