---
title: "gedit is unable to detect character encoding?"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by horse@pples on 2010-09-20
"gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

So  am I to understand that if gedit doesn't recognize even one character  in a .txt file it refuses to open it? Not to be rude but that's just  dumb. Why not have it go thru the list of common encodings til it finds  one that will open it? Or do what notepad does and just replace the  unknown characters with a lil black rectangle? At one point I had  characters from several different sources and none of the encodings  would open the file so I had to go back to windows and search line by  line for the forbidden characters til I finally got the file to open in  gedit. Not opening a 15,000 character .txt file because of 1  unrecognized character makes no sense to me at all. If there's just one  chinese character and one arabic character on a page gedit is totally  useless.

I need to store .txt files on a thumb drive and transfer  them back and forth between Ubuntu and Windows (a school computer)  several times a day. Is there a notepad program that can do the job  without the silliness of manually searching for the correct character  encodings and/or checking every line for encoding purity? Something like winpad that recognizes URLs so they can be  clicked into a firefox tab would be ideal. 

Found TEA text editor in the Ubuntu Software Center. May this is what i need?
[http://tea-editor.sourceforge.net/](http://tea-editor.sourceforge.net/)

I  swear I'm trying real hard to make the switch to Linux but seemingly  trivial things like this are 'bout driving me buggy.  Thanks for any  help you can provide.

---

### Post by jtarin on 2010-09-20
> So am I to understand that if gedit doesn't recognize even one character in a .txt file it refuses to open it? 
The right tool for the right job as they say.  Gedit (and gnome 2.x) supports unicode by default (and very well). You probably just need to set the type to utf8 when choosing the file in your open file dialog. It's also worth verifying that your file is *actually* utf8, as some tools are misleading, and it's easy to be mistaken about this.

When you talk about strange characters in notepad or gedit and if you mean little squares with numbers in them, that probably just means you don't have a font installed that has the characters needed. Otherwise, if it's showing other random characters, it's probably the load setting you've used, as I mentioned above.

---

### Post by quadproc on 2010-09-20
> **horse@pples said:**
> 
So  am I to understand that if gedit doesn't recognize even one character  in a .txt file it refuses to open it?
That is true.

One easy way around this problem is to use a different editor that won't disqualify the file when it finds something that isn't a text character.  I would think that vi would be a candidate.

Incidentally, if you have self-extracting files to deal with, they usually consist of a script followed by a compressed file.  You can use *head -n <value>* to extract the beginning of the file and then gedit will be happy to work with that portion of the file.

quadproc

---

### Post by JamButty on 2010-09-20
Gedit is not nearly as tolerant as Notepad, true, but why should it be? 
OpenOffice Word processor is a lot more tolerant and can certainly handle words in any language without crashing, even if it can't immediate represent them without the correct language sets installed.

Anything so exotic that neither Gedit nor OpenOffice can stomach should be opened with a hex editor, if you really need to look inside. These are available for Linux.

---

### Post by horse@pples on 2010-09-21
Thanks for the thoughts everyone. Sorry if my piddly annoyance came thru in my request for help. I should've been more polite.

So far:
Tea was a bust. It didn't do what I needed at all.
Open Office is way more program than I want to use for simple .txt files. I'm on a netbook and it's pretty low on resources already.
Per quadproc's suggestion I found GVim in the software center and so far it's doing fine. Seems to be the right tool for the right job. If I can figure out how to get URLs to be clickable into FF tabs I'll be set. Should be possible shouldn't it? i'll peck around with it for a while and see what I stumble into.

Thanks again.

---

