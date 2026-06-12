---
title: "The dictionary"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by ArnsteinK on 2009-04-09
Is it any way I can get nynorsk(norwegian) dictionary? If there isn't one already, is it a way to import this one: [http://www.dokpro.uio.no/ordboksoek.html](http://www.dokpro.uio.no/ordboksoek.html) to the Ubuntu dictionary-application?

---

### Post by fabricator4 on 2009-04-10
There's three Norwegian languages supported, a generic Norwegian which you probably have installed now, a Nynorsk Norwegian, and a Bokmal Norwegian.

If you intall the Nynorsk Norwegian you _should_ get the relevant dictionary.

Go System->Administration->Language Support.

It may ask if want additional language support installed.  Say "yes".

My understanding is that you only get the dictionary for the language you have selected.  I've seen complaints that it should be possible to have several dictionaries enabled at the same time. 

Chris.

---

### Post by Didius Falco on 2009-04-10
> **ArnsteinK said:**
> Is it any way I can get nynorsk(norwegian) dictionary? If there isn't one already, is it a way to import this one: [http://www.dokpro.uio.no/ordboksoek.html](http://www.dokpro.uio.no/ordboksoek.html) to the Ubuntu dictionary-application?

If you open a terminal window and type in (or cut and paste this)  ```
sudo apt-get install wnorwegian
```

It will install a Norwegian dictionary.

I hope this helps...

---

### Post by mvalviar on 2009-04-10
Related to the dictionary...Is there a way to put it in the global context menu? That is when I select a word anywhere I can right-click then select define word?

---

### Post by Didius Falco on 2009-04-10
> **mvalviar said:**
> Related to the dictionary...Is there a way to put it in the global context menu?

I couldn't find a way to do that.You can, however, add it to the panel and just cut/paste the word you are looking for to it.

Not quite as convenient, but still easier than getting up to go get the printed one. <G>

---

### Post by ArnsteinK on 2009-04-10
I checked the settings, and the only dictionaries I can find is longdo thai-english and some spanish dictionaries.

---

### Post by ArnsteinK on 2009-04-10
Bump

---

### Post by Didius Falco on 2009-04-10
Try going to "System/Administration/Language Support".

 Click the "Install/Remove Languages" button and and it will open it to your default language. If that is    Norwegian Nynorsk, then take a look at the "Components" listed at the bottom. Tick the boxes that apply.

I just took a look at the Norwegian, Nynorsk on my (English default) system, and it offers "Basic Translations" (for the desktop), "Extra Translations" (Open Office, Firefox, Thunderbird, Gaim translations and help files), and "Spellchecking and Writing Aids" (Word Lists, Dictionaries, Thesauruses, etc.).

There are other options, but they were greyed out on my system.

If you are using something else by default, scroll down the list to Norwegian, Nynorsk, click the box next to it to install the language files and tick the Component boxes as described above.

Try this out and let us know how it works out.

---

### Post by ArnsteinK on 2009-04-10
Yeah, my Ubuntu is in nynorsk, but I'm thinking of Programs->Office->Dictionary! That's only in english.

---

### Post by Didius Falco on 2009-04-10
I tried various searches to see if I could find a Nynorsk dictionary for the Gnome Dictionary. Unfortunately, I was unable to find one.

I even added Norwegian Nynorsk to my languages and tried to changed the Gnome dictionary to it, with no luck.

If you can find an online source (maybe contact that online one from your very first message) and find out if they do/would support adding it to the Gnome dictionary applet, you can get instructions on how to do so from the applet help file, under section 4, Preferences.

I'm afraid I've reached the limits of my ability to help you with this. Hopefully, someone else can step in and help you with this...

---

