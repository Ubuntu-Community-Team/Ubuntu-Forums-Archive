---
title: "Easy Ways to Produce Characters that Aren't on Your Keyboard"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by rewyllys on 2010-02-26
This post summarizes methods that work for me for inserting non-US-keyboard characters in documents, when I'm using Gnome in Ubuntu 9.10.  I've written this in terms of US standard keyboard layouts because that's what I use, but the methods also apply to people using other keyboard  layouts.

These methods consist of:[INDENT]  (A) ways to insert Unicode codes for non-US-keyboard characters, such as the Greek upper- and lower-case gamma (&#915;, &#947;), along with other symbols, such as that for the integral sign (&#8747;); and

(B) easy keyboard combinations for many alphabetic characters that include diacritics, or "accent marks" (e.g., as on è, é, ë, and ê).  Some symbols and non-US-keyboard characters can be produced this way.  Note: Some accented letters (e.g., the Czech &#268; and &#353;) require method (A).
[/INDENT]**Concerning Method A: Inserting Unicode Codes**

 The starting point for me was a posting by abehrens[INDENT][http://ubuntuforums.org/showthread.php?t=329987&page=2](http://ubuntuforums.org/showthread.php?t=329987&page=2)
[/INDENT]that deals with ways to utilize Unicode representations. The posting says:[INDENT]  Applications that use newer GTK+ libraries (which includes all applications written for Gnome) require a "U" before the Unicode digits. Either of the following sequences should work:[INDENT]  [1] Ctrl-Shift-U, *hex codes*, Spacebar

[2] Hold down Ctrl-Shift, U, *hex codes*, release Ctrl-Shift
[/INDENT][/INDENT]I've found abehrens's second sequence more convenient for me. I interpret it as saying:[INDENT]  While holding down Ctrl-Shift, press, in succession, U followed by the desired symbol's hexcode characters (in doing this, the alphabetic characters are, in effect, entered in lower-case); then release Ctrl-Shift.
[/INDENT]For example, the integral sign, &#8747;, has the Unicode representation: 222B.  Hence, to obtain the integral sign, you can do the following:[INDENT] [press and hold down] Ctrl-Shift, [press in succession] u222b, [release] Ctrl-Shift
[/INDENT]Note: When using OpenOffice, you must also press ENTER *after* the four code characters and *before* you release Ctrl-Shift.

Abehrens's second sequence works on my laptop (an IBM [now Lenovo] Thinkpad T42), which lacks a separate numeric keypad; and it works on my destop, whose keyboard includes a numeric keypad.

 **Concerning Method B: Using Keyboard Short-Cuts**

 For many accented letters, and for some symbols and non-US-keyboard characters, there are easy keyboard short-cut combinations that can yield the desired result.  These share the following process:

You strike a *Compose* key (I'll explain in a moment what the *Compose* key is) followed by two keyboard letters or symbols, which I'll call "key1" and "key2" herein.  The *Compose* key tells Gnome to combine the next two letters or symbols and to interpret the combination in such a way as to yield a single letter or symbol. 

For example, you can use such sequences as the following:[INDENT]*Compose*, *"~"*, "n" to yield the Spanish lower-case n with tilde, ñ
*Compose*, "o", "a" to yield the Swedish lower-case a with ring above, å
*Compose*, "/", "L" to yield the Polish upper-case L with stroke, &#321;
*Compose*, "-", "L" to yield the British pound symbol, £
*Compose*, "-", "+" to yield the plus-or-minus sign, ±
[/INDENT]To help myself remember the combinations, I find it convenient to think of the underlying pattern as[INDENT]*Compose*, modifying key (key1), key being modified (key2)
[/INDENT]because in many cases, the key1 symbol is added, in a fairly obvious way, to the key2 symbol, as in the examples just given.  There are exceptions in which the resultant symbol is--at least, to my way of thinking of it--a "balanced" pairing of the key1 and key2 symbols: e.g., the sequences[INDENT]*Compose*, "T", "H" to yield the Icelandic upper-case thorn, Þ
*Compose*, "t", "h" to yield the Icelandic lower-case thorn, þ
*Compose*, "s", "s" to yield the German lower-case double-s (also known as eszset or sharp-s), ß
*Compose*, "a", "e" to yield the lower-case ligature, æ  
[/INDENT]Most of these "balanced pair" combinations have their own logic, as the foregoing examples attest.

 **What Is the *Compose* Key?**

 Gnome offers several possible choices for the *Compose* key.  To make your choice, use System > Preferences > Keyboard, and in the resulting "Keyboard Preferences" window, select the Layout tab. This will open a "Layout" window, in which you click on "Options" and then on "Compose key position".  This will reveal the possible choices, and you should think about which of them will be most convenient for you.  (Don't fret too long over the choice; you can easily change your mind later.)

As the *Compose* key, I chose the Menu key (the key between the right Windows key and the right Ctrl key) for my desktop, and the CapsLock key for my laptop.  I made these choices because the Menu key has almost no other uses for me, and because my laptop lacks a Menu key.  (My choice of Caps Lock as the *Compose* key for my laptop has the minor inconvenience of precluding my using it for its original purpose; but I'm willing to sacrifice that for the great convenience, to me, of using it as the *Compose* key.)

The "*Compose* key, key1, key2" method has a surprising number of possible "key1, key2" combinations that yield useful results.  When I need a shortcut for a symbol that I haven't used before, I just try plausible combinations, hoping that one of them yields what I need. All the usable combinations I'm aware of strike me as logical and having mnemonic value; guessing them has been reasonably easy.  (A table of all the *Compose-*key-sequence possibilities exists, as discussed in the Addendum below.)

 **Summary**

 Here's a summary of what I recommend:[INDENT]  1.   When you need to use a non-US-keyboard character, see if if can be produced via a *Compose*-key-sequence (i.e. via Method B), either by[INDENT]  1.1  Trying plausible combinations, or by
1.2  Looking in the *Compose*-key table to determine whether a *Compose*-key-sequence exists for the desired character.
[/INDENT]2.  If no *Compose*-key-sequence exists for the desired character, look up the Unicode code for the desired character, and use Method A to insert that code.
[/INDENT]**Conclusion  **

 For all characters and symbols, you can, of course, use the Gnome Character Map applet (*gucharmap*).  (For convenience, I've added it to my panel.)  But for most of the characters and symbols that I use frequently, I find it quicker to use the methods I've discussed above.  I prefer to use Method B if a *Compose*-key sequence is available; if not, I use Method A, the Unicode method.  (Hint: For the symbols I use frequently that require Method A, I've printed out a list of the symbols and their Unicode codes; and I keep it taped to the edge of my monitor.)

 **Addendum**

 In the "Ubuntu Documentation > Community Documentation > ComposeKey" Webpage, whose URL is[INDENT][https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)
[/INDENT]I found the following information:[INDENT]  Gnome
  The compose key sequences used by Gnome are derived from the X compose tables of XFree86 version 4.0 with further modifications to provide a Gnome standard for all locales. They are hard coded into the program in source file gtk+-2.10.7/gtk/gtkimcontextsimple.c 
[/INDENT][INDENT]
[LIST]
[*]**[GtkComposeTable]("https://help.ubuntu.com/community/GtkComposeTable")**     lists the *Multi_key* part of the Gnome Compose Key table.
[*]**[GtkDeadKeyTable]("https://help.ubuntu.com/community/GtkDeadKeyTable")**     lists the *dead key* combinations of the Gnome Compose Key     table.
[/LIST]
[/INDENT]The full contents of the GtkComposeTable are available at:[INDENT][https://help.ubuntu.com/community/GtkComposeTable](https://help.ubuntu.com/community/GtkComposeTable)
[/INDENT]The full contents of the GtkDeadKeyTable are available at:[INDENT][https://help.ubuntu.com/community/GtkDeadKeyTable](https://help.ubuntu.com/community/GtkDeadKeyTable)
[/INDENT]The "Ubuntu Documentation > Community Documentation > ComposeKey" Webpage also explains how to select and use Third-Level and Fourth-Level *choosers* for keyboards.  Utilizing these *choosers* provides still more ways to enter non-US-keyboard characters.

---

### Post by patocardo on 2010-03-11
I am also using Ubuntu 9.10, but compose key do not do anything, no matter what key I assign to it. Is there other step to make it works?

---

### Post by khughitt on 2010-04-22
I'm also not having any luck input special characters. I tried out the suggestions in both

[http://wiki.linuxquestions.org/wiki/Accented_Characters](http://wiki.linuxquestions.org/wiki/Accented_Characters) and
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

with no luck. My language is set to utf-8.

Any ideas?

---

### Post by agnes on 2010-04-22
Another method is, you could edit Xmodmap configuration to get special characters. 
This is explained on a Puppy forum post number 4 [here]("http://www.murga-linux.com/puppy/viewtopic.php?t=49008&sid=82631e3b408bb9f4f4e870000745cc0d") (webpage might load slow).
For example you could have
*keycode  38 = a A aring Aring* in it.
That would give me the a with a circle above it (å) if I typed AltGr+a, and the A with a circle above it if I typed AltGr+Shift+a.

You can also edit the (first) modifier key mentioned in that post with xmodmap, but default it should be Alt or AltGr for USA-keyboards (*xmodmap -pm* shows you it.). I don't remember now how to edit the modifier key but if you really need to you could google it. 

A list of keycodes you can enter in the .xmodmap config file is [here]("http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap").

You need to load the .xmodmap config file then at logon see [here]("http://ubuntuforums.org/showthread.php?t=367583").

If you don't know the keycode of the key you need to edit use xev ([here another tutorial]("http://dev-loki.blogspot.com/2006/04/mapping-unsupported-keys-with-xmodmap.html")).

I must say I only tried this with Puppy but it should work ok on Ubuntu and also other Linux distros.

---

### Post by simosx on 2010-05-06
> **pwnedd said:**
> I'm also not having any luck input special characters. I tried out the suggestions in both

[http://wiki.linuxquestions.org/wiki/Accented_Characters](http://wiki.linuxquestions.org/wiki/Accented_Characters) and
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

with no luck. My language is set to utf-8.

Any ideas?

You need to verify that you have configured the ´compose´ key according to the instructions above.
If you did it correctly, then the command

[INDENT]gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
[/INDENT]

should output something like

 layouts = [us]
 options = [grp	Compose key	compose:menu]
 model = 

which means the compose key is the 'Menu' key (in my case).

Then, try out with Menu + ' + a = á 
or Menu + (  then type '10)' = &#9321;.

---

### Post by steve_steve on 2012-10-15
Some alternate methods:

1) Add the 'character palette' to the panel (in 12.04 you hold the super-key [windows key] + alt + right-click to add to the panel.  Who knows why it isn't a simple right-click anymore).  After you've got it in the panel, you can right-click the character palette and select 'preferences' and get other sets of special characters.  You could probably add more than one character palette with different characters if you feel like filling up the panel.

2) Go to any web page with a list of special characters.  Copy & paste into gedit.  Save, then copy & paste characters from that text file.  Obviously not so useful if you need special characters very often, but ok for once in a while.

---

