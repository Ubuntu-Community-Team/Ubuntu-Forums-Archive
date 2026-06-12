---
title: "OpenOffice Calc Question"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by Patricrawley on 2009-08-02
I made a bank account spread sheet with deposit, withdrawal and balance columns. I know that I can just use that drag function to apply the formula to more cells down the column. I was wondering if there was a way to make it so that it doesn't appear until I add something into the row, so I don't have my balance repeating constantly in a columns.

---

### Post by llamabr on 2009-08-02
Hi.  This isn't really an ubuntu question -- it's an openoffice one.

If you don't get a hit here, maybe take your question to  that forum.

good luck.

---

### Post by squenson on 2009-08-05
In the future, you should ask OpenOffice Calc questions to the official OpenOffice forum: [http://user.services.openoffice.org/en/forum/](http://user.services.openoffice.org/en/forum/)

If you have the debit and credit entries in the column A and B, and the balance in column C, then you could use a formula for the balance like:

=IF(AND(A3="";B3="");"";C2+B3-A3)

It will show an empty cell unless you enter a debit or credit.

---

### Post by MrWES on 2009-08-05
> **squenson said:**
> In the future, you should ask OpenOffice Calc questions to the official OpenOffice forum: [http://user.services.openoffice.org/en/forum/](http://user.services.openoffice.org/en/forum/)

If you have the debit and credit entries in the column A and B, and the balance in column C, then you could use a formula for the balance like:

=IF(AND(A3="";B3="");"";C2+B3-A3)

It will show an empty cell unless you enter a debit or credit.

This works too; edit the cells to meet your needs.

```
=IF(AND(ISBLANK(F6),ISBLANK(G6)),"",H5-F6+G6)
```

Bill

P.S. If you want the sheet, private message me with your email address and I send it to you.

---

### Post by Zill on 2009-08-05
Patricrawley:  If you want to try an existing application rather than create your own spreadsheet then [GnuCash]("http://www.gnucash.org/features.phtml") is worth a look.

---

### Post by MrWES on 2009-08-05
> **Zill said:**
> Patricrawley:  If you want to try an existing application rather than create your own spreadsheet then [GnuCash]("http://www.gnucash.org/features.phtml") is worth a look.


Also,there is a small foot print program, mutli-platform, called Homebank. I use it on both my Windows and Ubuntu machines.

It's available in the repositories:

```
sudo apt-get install homebank
```
[http://homebank.free.fr/]("http://homebank.free.fr/")

---

### Post by Patricrawley on 2009-08-05
I've already created my own spreadsheet, using your ifblank cell. Thanks!

---

