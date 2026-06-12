---
title: "OpenOffice Writer and Columns"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by asharpham on 2010-02-26
I have a document where one section requires 3 columns. I created the columns and want to restrict this section to about a third of a page. However, when I enter text into column 1, it continues increasing the size of the section without flowing the text into the second column. How do I restrict the columned section from increasing in size?

Alan.

---

### Post by laidback on 2010-02-27
Forgive me if I haven't understood exactly the problem, but would you be better off using merge cells...format>merge cells. This can be applied over several columns but for as many rows as you need. Result is 1 cell per row within the selection.

Or

Would format>cells>alignment>wrap text automatically (tick box)
work for you. This would keep columns the same width but allow rows to expand if necessary.

---

### Post by JackRock on 2010-02-27
> **laidback said:**
> Forgive me if I haven't understood exactly the problem, but would you be better off using merge cells...format>merge cells. This can be applied over several columns but for as many rows as you need. Result is 1 cell per row within the selection.

Or

Would format>cells>alignment>wrap text automatically (tick box)
work for you. This would keep columns the same width but allow rows to expand if necessary.

He's talking about columns, not cells.  He's not using a table.


OP, are you referring to the size being increased vertically, or horizontally?  If horizontal, did you uncheck "AutoWidth" in Format > Page > Columns?

---

### Post by SecretCode on 2010-02-27
And if vertically, did you check 'evenly distribute contents to all columns'? When that's unchecked it goes to the bottom of the page before wrapping to the next column.

---

### Post by DeadSuperHero on 2010-02-27
One way that I create column is by manually drawing text boxes on a page.

View>Toolbars>Drawing

And a "Text" button will be on the bottom toolbar. It works just like in Microsoft Office, click and drag.

---

### Post by asharpham on 2010-02-28
Thanks guys. Yes, it is columns not a table. I'm sure at least one of those suggestions will solve my problem. But since I posted this, I've lost Ubuntu. I have it on a thumb drive and somehow it's become corrupted and won't load. I can still get into Windows so reluctantly I have to go back there to access the net.

Alan.

---

### Post by SecretCode on 2010-03-01
Remember you can install openoffice on windows!

---

### Post by asharpham on 2010-03-02
Yeah thanks. I don't need it on Windows as I have Microsoft Word. And I have no problems with the columns in Word but I want to use OpenOffice once I get Ubuntu up and running again. I eventually want Ubuntu to be the OS of choice and get rid of most of my Windows stuff.

Anyway, since last writing, I can no longer get into Windows as the gateway with the menu options no longer works. Something's gone wrong with my Ubuntu boot up and I now have to use the CD to get into Ubuntu. Anyone know where I'd find my documents on the Ubuntu drive as I can still access it even though it doesn't boot up any more.

Alan.

---

### Post by HereInOz on 2010-03-02
Your documents in Ubuntu are probably in:

/home/{username}/

Where {username} is your log in name.

---

### Post by asharpham on 2010-03-05
I resurrected Ubuntu and tried one of these suggestuions which worked wonderfully well. Thanks for all your help.

Alan

---

