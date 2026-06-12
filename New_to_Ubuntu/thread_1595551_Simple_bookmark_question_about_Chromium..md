---
title: "Simple bookmark question about Chromium."
date: 2010-10-13
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-10-13
I have been using Chromium lately and love how fast it is.  However, it seems to have all of my bookmarks from Firefox from when I FIRST installed it.  I have ran the "import from Firefox" and it works, but the bookmarks toolbar does not seem to update.

I tried to purge chromium-browser and reinstall via terminal, but the same issue persisted.

Here is what I need to do: COMPLETELY remove anything and everything to do with Chromium, or completely reset it, and reinstall it so that it prompts me to import as a "first time use" so that I can import my now completely updated bookmarks from Firefox.

Please advise as to the location of what exactly I need to delete, because I did not see a .chromium folder in /etc or my home folder after removing Chromium, but the settings must still be somewhere.

Thank you.

---

### Post by ddarsow on 2010-10-13
```
sudo apt-get purge chromium-browser
```

You mean that this does not work??

---

### Post by x C0MMAND0 x on 2010-10-13
I already ran that exact purge command, but even after I did that and re-installed it, the browser still had the original bookmarks and not the new ones, and it didn't prompt me to import anything like a "first time run", and even after manually adding the bookmarks it didn't update either.

Thank you though, any other ideas?

---

### Post by x C0MMAND0 x on 2010-10-14
Bump

---

### Post by x C0MMAND0 x on 2010-10-15
Anybody?

---

### Post by TeoBigusGeekus on 2010-10-15
Delete the ~/.config/chromium folder.
When you uninstall software, their specs folders remain in your system.

---

### Post by aala on 2010-10-15
just go from nautilus to...

/home/your-user-name/.config/chromium/Default

and delete de 'Bookmarks' and 'Bookmarks.bak' files (without the '').

Hope it helps!... hey! I almost forget chromium needs to be closed.

---

### Post by x C0MMAND0 x on 2010-10-26
Thank you!

---

