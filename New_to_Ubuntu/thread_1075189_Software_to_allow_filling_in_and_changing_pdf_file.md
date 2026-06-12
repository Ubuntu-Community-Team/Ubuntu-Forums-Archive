---
title: "Software to allow filling in and changing pdf files."
date: 2009-02-20
forum: New to Ubuntu
---

### Post by egalvan on 2009-02-20
I am looking for software that will allow filling in pdf-style forms,
and then save them.

I have used evince, and this lets me fill the forms, but not save them. Which means I cannot go back and make changes/corrections.

Anything available?

ErnestG


n.b.
most of these forms are downloaded from government websites.
These are used in place of paper forms.

---

### Post by baracuda68 on 2009-02-20
You can try PDFedit.
I believe it is in the repos'.
There is a Souceforge page for it. or Google it.

It is a little "harsh" or " crude" (for me)or whatever I would call it, but I think this is what you are looking for.

---

### Post by hyper_ch on 2009-02-20
java based but works fine:  [http://www.cabaret-solutions.com/en/products/stage/bundle_home](http://www.cabaret-solutions.com/en/products/stage/bundle_home)

---

### Post by egalvan on 2009-02-20
> **baracuda68 said:**
> try PDFedit.
it is in the repos'.
There is a Souceforge page for it. or Google it.

It is a little "harsh" or " crude" (for me), but I think this is what you are looking for.

I tried this.

It died a cruel death when I tried to open a pdf.

```
pdfedit
Error (2): Unknown compression method in flate stream
pdfedit: treeitempdf.cc:112: void gui::TreeItemPdf::observePageDict(): Assertion `pageDictionary.get()' failed.
Aborted
```

Ny quest continues.

---

### Post by egalvan on 2009-02-20
> **hyper_ch said:**
> java based but works fine:
[http://www.cabaret-solutions.com/en/products/stage/bundle_home](http://www.cabaret-solutions.com/en/products/stage/bundle_home)

I tried this.

It too died a cruel death; when I attempted to download the app

```
Sorry!
It seems you have requested a page no longer available or an unexpected error has occured processing your request.

Please, report the broken link or your recent activities to our support team.

You can try to look up the resource you tried to find using the "Search" utility for this website. 
```

My quest continues.

---

### Post by hyper_ch on 2009-02-20
download works fine here.

---

### Post by Pollox on 2009-02-20
I just tried the program hyper_ch recommended, and it seems to work great for filling out forms.  The download page is [http://www.cabaret-solutions.com/en/downloads/linux](http://www.cabaret-solutions.com/en/downloads/linux).  Just select 32 or 64 bit, then select "Ich stimme zu" to accept the license agreement.  I have no idea why the agreement is in English and the rest of the page in another language.

---

### Post by egalvan on 2009-02-20
> **Pollox said:**
> I just tried the program hyper_ch recommended, and it seems to work great for filling out forms.  The download page is [http://www.cabaret-solutions.com/en/downloads/linux](http://www.cabaret-solutions.com/en/downloads/linux).  Just select 32 or 64 bit, then select "Ich stimme zu" to accept the license agreement.  I have no idea why the agreement is in English and the rest of the page in another language.


Followed your link,
selected 32bit,
selected "Ich stimme zu"
Again, the same error as before....

```
Sorry!
It seems you have requested a page no longer available or an unexpected error has occured processing your request.

Please, report the broken link or your recent activities to our support team

You can try to look up the resource you tried to find using the "Search" utility for this website.
 
last update: 07/24/2007 13:05 by admin 
```


What can I say?

---

### Post by egalvan on 2009-02-20
I noticed this is a *.tar.gz* file.

If I ever get it on my drive, what would the steps be to 
unpack and install?

Still trying to d'ld.

Thanks

ErnestG

---

### Post by stalkingwolf on 2009-02-20
If I change the language to english i get that error.  If however I
use the german it works fine.

---

### Post by ussndmac on 2009-02-20
I thought the latest OpenOffice could edit PDF?

No?

---

### Post by Captain Legless on 2009-02-20
I've managed to do some editing of PDF files using Open Office. There's a bit of fiddling needed but it is possible to open pdf files in "Draw" then export them as a pdf.

Check out this link :- [http://www.linux.com/feature/139588]("http://www.linux.com/feature/139588")

You will need Open Office 3.O and the Sun pdf Import extension.

---

### Post by hyper_ch on 2009-02-21
> **egalvan said:**
> I noticed this is a *.tar.gz* file.

If I ever get it on my drive, what would the steps be to 
unpack and install?

Still trying to d'ld.

Thanks

ErnestG

unpack it an then you get an installer .bin or .sh file... or something... I don't remember but it was easy to install.

---

