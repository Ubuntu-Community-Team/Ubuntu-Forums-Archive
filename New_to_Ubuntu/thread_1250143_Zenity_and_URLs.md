---
title: "Zenity and URLs"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by AlwaysLearning on 2009-08-26
Ok, the Zenity man page is pretty light-on when it comes to this sort of info. I'm hoping someone can shed some light on this...

I'm trying to get Zenity info and progress dialogs to display URLs, but come up against various errors if they contain special characters, such as:

(zenity:1776): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 4: Character '=' is not valid inside an entity name

It also drops the --text content and just displays "Running..." in its place. Rinse and repeat for '&', '=' and '%' which, unfortunately, are all fairly common characters in URLs. I've tried using sed to encode the URLs to escape the nefarious characters but don't seem to have any luck with common encodings such as '\=', '\\=', '\x3d', etc.

Anyone have any ideas on how to proceed from here?

```
#!/bin/sh
export DEMO_SRC="http://example.org/demo.cgi?foo=bar&baz=%2e"
export DEMO_DST=Somefile.txt
echo SRC: $DEMO_SRC
echo DST: $DEMO_DST
zenity --progress --pulsate --title="Downloading..." --text="From:\\n$DEMO_SRC\\n\\nTo:\\n$DEMO_DST"

```

---

### Post by lswb on 2009-08-26
Don't know the complete answer but if you replace the '&' character in DEMO_SRC with '&amp;' it will display without errors.

---

### Post by AlwaysLearning on 2009-08-26
> **lswb said:**
> Don't know the complete answer but if you replace the '&' character in DEMO_SRC with '&amp;' it will display without errors.

Actually, that seems to be the complete answer.

It looks as though Zenity was choking on the '=' and '%' characters if they came after an '&' character as, in the example above, '&bar=' is not a valid HTML entity name. (Now the error message makes sense.) So all that was needed was the following:

```
#!/bin/sh
export DEMO_SRC="http://example.org/demo.cgi?foo=bar&baz=%2e"
export DEMO_DST=Somefile.txt
export DEMO_SRC_ENCODED=$(echo $DEMO_SRC | sed "s/&/&amp;/g")
echo SRC: $DEMO_SRC_ENCODED
echo DST: $DEMO_DST
zenity --progress --pulsate --title="Downloading..." --text="From:\\n$DEMO_SRC_ENCODED\\n\\nTo:\\n$DEMO_DST"

```

Thanks, lswb!

---

### Post by lswb on 2009-08-26
What's surprising to me that zenity apparently uses a gtk library string display function that reacts to a possible url string by checking if it is valid and throwing an error if not. I would expect zenity to simply display any string passed to it. It may be farfetched, but suppose you were using zenity to display a string created by some other program and that string happened to be an invalid url? Imagine tracking *that* bug down!

---

### Post by AlwaysLearning on 2009-08-27
Interesting, indeed. The entity name error prompted me to carry out a little experiment...
```
#!/bin/sh
export DEMO_TXT="<b>Bold</b>\\n<i>Italic</i>\\n<u>Underline</u>"
echo TXT: $DEMO_TXT
zenity --progress --pulsate --title="Foo Bar Baz" --text="$DEMO_TXT"
```
It seems that Zenity has half an HTML interpreter behind its GTK string functions. It understands basic things like bold, italic and underline, but can't handle <br> or <br /> tags (you can achieve the same thing with \\n though). It definitely can't handle <img> tags. :)

I wonder what other magic is in there?

---

### Post by lswb on 2009-08-27
I didn't even think about using markup on the displayed text! A nice feature but it sure would be nice if the zenity man page or docs mentioned it. I wonder if there is an option to turn it off? Suppose you wanted to display a literal string like "<b> is the opening tag for bold text"  ? I just tested that and sure enough it complains about a markup error because of no closing tag in the string! Using &lt; and &gt; instead of < > it displays OK. So I guess the lesson is don't depend on using zenity to display dynamically created strings if their contents might have some unknown subset of markup tags!

---

### Post by AlwaysLearning on 2009-08-28
Ok, I downloaded the Zenity source and did some poking around. It looks as though having Gtk.Labels with the "use_markup" option set have enabled the Pango Markup Language to be used. See:
[http://library.gnome.org/devel/pygtk/stable/pango-markup-language.html](http://library.gnome.org/devel/pygtk/stable/pango-markup-language.html)

The span tag in particular lets you do some interesting stuff, but you need to watch the use of double-underlines on the last line of text (it gets clipped by the viewport so it looks like a single underline) - you can fix that with an extra \\n on the end.

Doesn't explain why &entities; are involved, but you can still do some interesting things with it.
```
#!/bin/sh
################################################################################
# Gtk.Label (Pango) markup that works with Zenity:
# b, big, i, s, small, span, sub, sup, tt, u
################################################################################
export DEMO_TXT="<b>Bold</b>\\n<big>Big</big>\\n<i>Italic</i>\\n<s>Strikethrough</s>\\n<small>Small</small>\\n<sub>Subscript</sub>\\n<sup>Superscript</sup>\\n<tt>Teletype</tt>\\n<u>Underline</u>\\n<span background=\"#007f00\" font_desc=\"WebDings Italic 24\" foreground=\"#ff7f7f\" stretch=\"ultraexpanded\" strikethrough=\"true\" underline=\"double\" variant=\"smallcaps\" weight=\"900\">Span Text</span>\\n"
echo TXT: $DEMO_TXT
zenity --info --title="Foo Bar Baz" --text="$DEMO_TXT"
```

---

