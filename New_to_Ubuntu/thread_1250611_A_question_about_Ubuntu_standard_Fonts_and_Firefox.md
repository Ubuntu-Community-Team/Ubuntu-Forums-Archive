---
title: "A question about Ubuntu standard Fonts and Firefox"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by elvin66 on 2009-08-26
I have just installed Ubuntu desktop and I must say I'm super impressed. Can't believe I didn't do this years ago. Move over Bill Gates ! Now to my problem.

I have only installed the standard Ubuntu and not added anything extra since my installation, however, when I view certain websites using Firefox, the font on that website is different than the actual font the web designer has specified. I understand this is because I don't have that font installed, however, I love the font that Firefox is defaulting to but don't know what it is. The web font is asking for Arial but I haven't installed it. The site is mine and when I view it through my Ubuntu boot, some of the text runs outside the tables. In order for me to rectify this, I need to install whatever font Ubuntu is using on my windows system so I can configure the table with that font. I love the font Ubuntu/Firefox is using but how do I find out which font it is and how can I copy this font to my windows drive?

Please help I'm going nuts trying to figure this out......  The website is [www.junktraders.co.nz]("http://www.junktraders.co.nz") if you want to look at it through Ubuntu and firefox.

---

### Post by jrothwell97 on 2009-08-26
Welcome to the Ubuntu forums!

Due to licensing restrictions, Ubuntu can't bundle the "standard" fonts, because the copyright for most of them is held by Microsoft.

However, you can easily install them with minimal effort. Go to System/Administration/Synaptic Package Manager, enter your password, mark "msttcorefonts" for installation and apply the changes. If that seems very long winded, you can take a shortcut and use the Terminal.

In Applications/Accessories/Terminal, type

```
sudo apt-get install msttcorefonts
```

It will ask for your password: when you type, nothing will appear (the cursor won't even move) but your password is still going in, so enter it as normal. The Microsoft fonts should then be installed, and all you should have to do is restart Firefox (if this doesn't work, try logging out and then back in).

Good luck!

---

### Post by elvin66 on 2009-08-26
> **jrothwell97 said:**
> Welcome to the Ubuntu forums!

Due to licensing restrictions, Ubuntu can't bundle the "standard" fonts, because the copyright for most of them is held by Microsoft.

However, you can easily install them with minimal effort. Go to System/Administration/Synaptic Package Manager, enter your password, mark "msttcorefonts" for installation and apply the changes. If that seems very long winded, you can take a shortcut and use the Terminal.

In Applications/Accessories/Terminal, type

```
sudo apt-get install msttcorefonts
```

It will ask for your password: when you type, nothing will appear (the cursor won't even move) but your password is still going in, so enter it as normal. The Microsoft fonts should then be installed, and all you should have to do is restart Firefox (if this doesn't work, try logging out and then back in).

Good luck!
Hey thanks a lot dude for that info. I'll go give that a try. My main question was to find out what font Ubuntu is actually using when I opened he webpage that asks for "Arial". I like the font it is using but I need to edit the webpage and change the font from Arial to [whatever firefox is using]. If I could do that, I would be very happy !

---

### Post by jrothwell97 on 2009-08-26
I wouldn't really recommend that: generally, if a program can't find a font that is specified in a web page, it'll look for the closest substitute.

If you like the font, though, try taking a screenshot of Firefox using that font and we should be able to identify it. (You can use Applications/Accessories/Take Screenshot.)

---

### Post by winotree on 2009-08-27
I may be way off on giving this as an answer, but have you checked inside Firefox for the font it's using?  Try this:  Menu | Edit | Preferences | Content | Font and Colors | Advanced  and see if there is something there to help answer your question.  

You could also check or uncheck the option: Allow pages to choose their own fonts, instead of my selections above.  Like I said, I hope this helps you.  If I'm in error please tell me...  ;)

---

