---
title: "No text display in Firefox 3"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by barbet on 2008-11-13
A strange problem with Firefox 3 under Intrepid.

Some portions of text, in any page, are not displayed. It seems to be normal text (not emphasized).

I try to fully uninstall Firefox 3 and install it again: no change!

But if I choose "no style" to display the page, the whole text appears, but not styled :-(

The problem is with "Page Basic Style".

An idea?

---

### Post by quimico69 on 2008-11-13
perhaps you can try CTRL - (minus) to reduce the font size.  I've seen cases where font size and CSS formatting don't get along well.

Just a thought.

---

### Post by barbet on 2008-11-13
> **quimico69 said:**
> perhaps you can try CTRL - (minus) to reduce the font size.  I've seen cases where font size and CSS formatting don't get along well.

Just a thought.
Thanks a lot for your thought. But even at the lowest size the unvisible text remain unvisible!

---

### Post by lee-anna-loo on 2009-01-08
have anybody found a solution to this problem??

i'm experiencind the same thing from this morning and i cannot fix it.. 
i tried uninstalling the firefox and installing again but it doesn't help.. 

does anybody have any ideas what might help??

---

### Post by lee-anna-loo on 2009-01-08
--

---

### Post by fsierra3 on 2009-01-16
I have a similar problem. a few days ago some pages started to be displayed without text, not in all user accounts, but in the ones I created after installation.

---

### Post by fsierra3 on 2009-01-16
I installed Epiphany Gecko, to see if it displayed those pages (e.g. [www.uninorte.edu.co](www.uninorte.edu.co)) correctly, but that is no the case. It appears then that the problem is not in Firefox.

---

### Post by Atahualpa on 2009-01-17
I had copied fonts into /usr/share/fonts directly (not in subfolders). This caused the described problem for me. I solved it by removing any font from that directory (not from its subdirectories of course!!!).

---

### Post by fsierra3 on 2009-01-17
You can also solve the problem changing the font preferences:
Go to Edit->Preferences-> In Content tab->Advanced-> Uncheck Allow pages to choose their own fonts.

---

### Post by alc@raz on 2009-02-05
i install new fonts to /usr/share/fonts/truetype and this problem occurs. The problem was the rights, so i need to change the files to 644 and firefox sprint perfect.

---

### Post by bpeyser on 2009-07-22
For me I saw a problem like this on some pages, not all. I think I nailed down the source of my problem: it is certain CSS that fails--like:

.class
{
    font-size: 12pt;
    line-height: 20px;
}

It seems to work fine if both are px or if both are pt, but doesn't work as above. I am using the "NoSquint" page zoom add-on, but also had the problem with that disabled. I used the WebDeveloper add-on to edit the CSS and it displayed well if I changed that CSS.

Also, the problem I'm seeing looks like the text disappears, but actually its layout gets ruined so that the text appears in some strange place, or there is _much_ more space between lines than there should be. Another problem I saw was some CSS like this:

.class
{
    font: bold 9pt/30px Arial, Helvetica, sans-serif, Geneva, Verdana, ms sans serif;
}

Again, the 'font-size' is in pt (9pt) and the 'line-height' is in px (30px). If I changed it to 9pt/30pt it was OK (or 9px/30px). If I don't allow the page to choose fonts, the layout is still bad.

I also had this problem in Shiretoko (firefox 3.5) though I am using 3.0.11 now. Not sure the best place to report this problem--it only seems to happen in my Ubuntu (Jaunty) install, not under Windows. Any suggestion?

---

### Post by John95 on 2009-10-27
Thanx for the idea fsierra3. That works awesome!8-)

---

