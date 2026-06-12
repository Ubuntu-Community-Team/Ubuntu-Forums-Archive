---
title: "Different fonts in Evolution?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-04-22
How do I compose email in Evolution using different fonts?

---

### Post by sroland81 on 2009-08-11
Yes, Evolution is an overall great e-mail client, but it should be possible to allow the user to write an e-mail using different fonts... i need to write a newsletter with different fonts... what can i do? any ideas? i don't want to install another e-mail client because i'm too used to Evolution and is great!... another thing... when sending email in HTML format with couple of table cells with text, when recieved with another Evolution client, the line spacing is larger than the original sent mail... this make the whole newsletter nonsense... i need Evolution to be WYSIWYG... (What You Send Is What You Get).... 

cheers!!

Santiago.-

---

### Post by mcduck on 2009-08-11
Using different fonts in e-mail wouldn't make any sense. The receiver of the mail would have to have the exactly same fonts installed in his system to be able to see them. (and that's very rarely the case, even if you stick to the most common basic fonts.) Now, I knwo that some poipular e-mail clients include font selection, but they are built on assumption that everybody else would run the same operating system and use the same mail client, and even then the fonts will break if you try to use any font that wasn't included in the base install.

If you want to send formatted messages that really work on other people's systems your *only* option is sending PDF files. Nothing else includes fonts and maintains correct formatting in different systems.

E-mail is, at it's basics, just raw text data. All the formatting you see is done with HTML code, and HTML is only able to *suggest* what fonts to use for rendering if the font is available.

---

### Post by cjv8888 on 2009-08-11
> **mcduck said:**
> Using different fonts in e-mail wouldn't make any sense. The receiver of the mail would have to have the exactly same fonts installed in his system to be able to see them. (and that's very rarely the case, even if you stick to the most common basic fonts.) Now, I knwo that some poipular e-mail clients include font selection, but they are built on assumption that everybody else would run the same operating system and use the same mail client, and even then the fonts will break if you try to use any font that wasn't included in the base install.

If you want to send formatted messages that really work on other people's systems your *only* option is sending PDF files. Nothing else includes fonts and maintains correct formatting in different systems.

E-mail is, at it's basics, just raw text data. All the formatting you see is done with HTML code, and HTML is only able to *suggest* what fonts to use for rendering if the font is available.

Yes, but I still get the whinge from wife now and again about changing back to Windows because she could do different fonts and colours in Outlook Express.  I changed her to Thunderbird which can 'sort of' do different fonts but the types are not as good.  Any other ideas?

---

### Post by mcduck on 2009-08-11
If Thunderbird supports font selection, then simply install fonts your wife likes. (not that the mail's receiver would ever see them, but its often a good idea to do even pointless things to keep wives happy.. :))

The fonts don't come from the programs, they come from the operating system.

---

### Post by cjv8888 on 2009-08-11
> **mcduck said:**
> If Thunderbird supports font selection, then simply install fonts your wife likes. (not that the mail's receiver would ever see them, but its often a good idea to do even pointless things to keep wives happy.. :))

The fonts don't come from the programs, they come from the operating system.

Are there any other good font sets that can be installed apart from the ones which came with the system?

> (not that the mail's receiver would ever see them, but its often a good idea to do even pointless things to keep wives happy.. )
LOL

---

### Post by niteshifter on 2009-08-11
Hi,

The repository package "msttcorefonts" has this for it's description:
> Installer for Microsoft TrueType core fonts
This package allows for easy installation of the Microsoft True Type
Core Fonts for the Web including:

  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings


---

### Post by mcduck on 2009-08-11
> **cjv8888 said:**
> Are there any other good font sets that can be installed apart from the ones which came with the system?

You can install any TTF or OTF fonts you can find, and there are also several font packages available in the repositories.

The font format is exactly the same that is used in both Windows and OSX.

---

### Post by cjv8888 on 2009-08-11
Thanks.  I will have a look at these.:)

---

### Post by sroland81 on 2009-08-11
Hi all again, my wife is dealing with newsletters and her machine was getting no support and so i went there and installed Intrepid for my wife, the Windows copy was not original and was very crappy in performance. Now i'm the tech support for my wife and i discover that in marketing stuff women can do a lot and in fact they do things that i did not in my entire life! i.e. sending a newsletter (i'm scientist astronomer, a.k.a. my life is within gnome-terminal)... so i've been exploring the most obscure side of trying to find a newsletter software for ubuntu, trying to write an email in HTML format with colors and flowers and all things you can imagine! maan!! i've learned a lot! otherwise, my wife is using ubuntu for working! this include openoffice, evolution, firefox, spreadsheets, pdfs, and stuff.... i noticed that ubuntu lacks a newsletter designing software, there is nothing in repos. I installed kompozer that crashes me in a snap 5 seconds after launched when trying to poen recent files or change table properties and stuff, very very bad... i did not even mentioned kompozer to my wife, and evolution has some bugs like the one i reported 15 min ago ([https://bugs.launchpad.net/bugs/412031](https://bugs.launchpad.net/bugs/412031)), that in Intrepid, the background table color is ommited when you change it.

some suggestions regarding the newsletter composing?

Regards,

---

### Post by mcduck on 2009-08-11
Do you mean newsletter as in something that would be actually printed (or at least distributed in PDF form)? In that case [Scribus]("http://www.scribus.net/") is excellent tool for desktop publishing. Or if that's too complicated, [Inkscape]("http://www.inkscape.org/") is a great vector graphics editor and can be used for simpler publishing tasks as well. (both programs are available in Ubuntu's repositories)

With web-oriented publishing I really can't help, as I write my code by hand and while I know some available WYSIWYG editors by name I really can't say anything about how good they are..

---

### Post by blur xc on 2009-08-11
> **mcduck said:**
> Using different fonts in e-mail wouldn't make any sense. The receiver of the mail would have to have the exactly same fonts installed in his system to be able to see them. (and that's very rarely the case, even if you stick to the most common basic fonts.) Now, I knwo that some poipular e-mail clients include font selection, but they are built on assumption that everybody else would run the same operating system and use the same mail client, and even then the fonts will break if you try to use any font that wasn't included in the base install.

+1 for the MS ruled OS world.  If you compose an email in outlook- and send it to 100 people, there's a better than 90% chance that they will see it on another MS machine, w/ the same MS default fonts installed...

BM

---

### Post by mcduck on 2009-08-11
> **blur xc said:**
> +1 for the MS ruled OS world.  If you compose an email in outlook- and send it to 100 people, there's a better than 90% chance that they will see it on another MS machine, w/ the same MS default fonts installed...

BM

..and if you had installed any extra fonts, or some program like Photoshop that brings a large selection of fonts with it, you might happily use them in your emails but nobody would see them.

So even to use the basic Windows fonts you'd have to actually know which ones they are. Which is why I don't see the idea of having even the option to select fonts for emails as sensible thing, it only gives people the false idea of the receiver seeing the message like it was composed. Evolutions way of allowing different headers and text formats without actually defining any specific typeface is much closer to reality.

---

### Post by sroland81 on 2009-08-11
Newsletter i mean for example the one that you may receive from Sun Microsystems when you register vistualbox. It consists mainly in tables with images and text inside the cells, it is much like making a webpage with tables and stuff, but the evolution HTML composer is quite limited (i.e. different fonts, but with this thread this item may be disregarded, and table colors, backgrounds, and stuff... i noticed they do not work very well), the idea of an HTML newsletter is that you open the mail and it is rigth there, no attachments, no adobe to open it... no save as... folder.. and the open it. I would do this way (a.k.a. i like to save attachments in my HDD), but this people liks to open the mail and see the news right there. I noticed that many newsletters open images and jpgs from the web... not attached to the mail... i did not find the way to insert an image from web URL in evolution... It would be nice if evolution had a "newsletter" option when you start a new item in the main "new" menu.

Regards,

---

### Post by blur xc on 2009-08-11
> **sroland81 said:**
> Newsletter i mean for example the one that you may receive from Sun Microsystems when you register vistualbox. It consists mainly in tables with images and text inside the cells, it is much like making a webpage with tables and stuff, but the evolution HTML composer is quite limited (i.e. different fonts, but with this thread this item may be disregarded, and table colors, backgrounds, and stuff... i noticed they do not work very well), the idea of an HTML newsletter is that you open the mail and it is rigth there, no attachments, no adobe to open it... no save as... folder.. and the open it. I would do this way (a.k.a. i like to save attachments in my HDD), but this people liks to open the mail and see the news right there. I noticed that many newsletters open images and jpgs from the web... not attached to the mail... i did not find the way to insert an image from web URL in evolution... It would be nice if evolution had a "newsletter" option when you start a new item in the main "new" menu.

Regards,

like one of these?

BM

---

### Post by sroland81 on 2009-08-11
yeah!! how can i do to make a newsletter like taht! then > teach mi wife

---

