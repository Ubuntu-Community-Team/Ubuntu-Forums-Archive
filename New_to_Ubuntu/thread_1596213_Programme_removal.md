---
title: "Programme removal"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by lizandeen on 2010-10-14
I recently downloaded and installed a programme ( JBidwatcher-nothing wrong with it per se, just realized it wasn't for me ) The thing is I have now no idea of how to remove it! I've searched for the files to manually delete it but cannot find them-any idea where they might be? Thanks in advance, Lizandeen

---

### Post by amjjawad on 2010-10-14
> **lizandeen said:**
> I recently downloaded and installed a programme ( JBidwatcher-nothing wrong with it per se, just realized it wasn't for me ) The thing is I have now no idea of how to remove it! I've searched for the files to manually delete it but cannot find them-any idea where they might be? Thanks in advance, Lizandeen

System > Administration > Synaptic Package Manager
Type your root's password
On the top right search box, type the name of your application
Once you find it, right click and mark for removal
Then Apply

---

### Post by lizandeen on 2010-10-14
Thanks,tried that but no joy1 Tried the "search for files" option but no luck there either.

---

### Post by amjjawad on 2010-10-14
> **lizandeen said:**
> Thanks,tried that but no joy1 Tried the "search for files" option but no luck there either.

That program is installed already? or you just downloaded it?

---

### Post by AndyM3 on 2010-10-14
*How* exactly did you install it? From source? From a .deb file? Using apt-get?

---

### Post by mosaic2s on 2010-10-14
can also use terminal to remove.

sudo apt-get remove <app name>.

---

### Post by lizandeen on 2010-10-16
I downloaded it from the JBidwatcher home site and used Sun Java to install. I'm assuming it's not a single use type programme. Itrid the sudo remove but it said it couldn't find it.

---

### Post by beew on 2010-10-16
> **lizandeen said:**
> I downloaded it from the JBidwatcher home site and used Sun Java to install. I'm assuming it's not a single use type programme. Itrid the sudo remove but it said it couldn't find it.

Does it even show up in Synaptic? If not then it is probably installed in your home directory(Many third party apps are like that). In that case just have to delete the programs' directory. To make sure there is nothing left behind (like Desktop files) you can do a search and delete them manually.

---

### Post by bennachie on 2010-10-16
I assume that you downloaded JBidwatcher-2.1.2.jar and have been launching it as a Java applet in accordance with the instuctions on the web-site? If that's the case, it has never actually been installed in a way which would allow Synaptic (or Ubuntu Software Center, which sometimes offers an easier mechanism for removing installed software, especially when the packages in question have come in DEB format) to recognise and delete it.

The best approach would probably be to search for the file by name (under the Places menu) and simply delete it once found.

---

### Post by cariboo on 2010-10-16
If you still have the installer directory, there shouyld be an uninstall script there.

---

