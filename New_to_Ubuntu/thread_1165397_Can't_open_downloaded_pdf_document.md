---
title: "Can't open downloaded pdf document"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by ntu on 2009-05-20
After downloading a document which I wanted to automatically open I get this:

> /tmp/ClaimForm-1.pdf could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I have changed "preferences" to save files in the desktop but still get the same message. Could someone tell me how to fix this please?

---

### Post by ntu on 2009-05-20
All fixed. Found it in the tmp folder.

---

### Post by Didius Falco on 2009-05-20
> **ntu said:**
> After downloading a document which I wanted to automatically open I get this:



I have changed "preferences" to save files in the desktop but still get the same message. Could someone tell me how to fix this please?

Do you have "Document Viewer" listed as a choice? That should be the default viewer for PDF files.

If it isn't listed, go to Synaptic Package Manager (**System/Administration/Synaptic Package Manager**) and search for **evince** and install it.

Then you should be able to choose Document Viewer as the default to open PDF files. To set it as the default viewer, Right-click on a PDF file, go to **Properties** and then the **Open With** tab and click the Document Viewer radio button.

After that, PDF files will be opened by Document Viewer on by clicking them (single or double, depending on how you have your systen set up...)

I hope this helps...

Regards,

Didius

---

### Post by ntu on 2009-05-20
[QUOTE=Didius Falco;7316779]Do you have "Document Viewer" listed as a choice?

Thanks for your full response Didius. Where would I find "Document Viewer" listed?

---

### Post by Didius Falco on 2009-05-20
If it's installed, you should see it as a choice when you right-click a PDF file. See the instructions in my previous post.

As to where to find it on the menu, it wasn't shown by default on mine, but you can edit what does and does not show on your menus bu Right-clicking the menu and choosing Edit Menus.

You can go down the list of Folders and click/unclick the boxes next to each item to show/hide that menu listing.

On my Ubuntu 9.04 system, Document Viewer is in the Graphics folder - it was not listed by default, as you really don't need it to be since after you set the file types you want it to open, simply left-clicking them will open the file in it.

I find it helpful to Edit the menu listings to hide things I never use, rearrange the order of the listing and show things that were previously hidden. One of the more useful one that I made visible was the Control Center under the Systems folder. That puts most of the settings you'd use for configure your PC on one menu. Much easier than chasing around looking for them... 

Regards,

Didius

---

### Post by ntu on 2009-05-21
Thanks Didius. The tmp folder does not have a pdf file in it now to practice on, but I have bookmarked this thread for when I next download a pdf and want it to auto-open.

---

