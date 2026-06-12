---
title: "Data entry GUI"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by djmac on 2010-09-01
I am not really sure how to word what I am asking. Will give it a go . .. 

I would like to be able to create a data file in something other than gedit. I have made a fortran routine that requires a lot of data. At present you can either type the data manual in the terminal, or manually create a data file in gedit. Both are pretty poor options when you are constantly changing some of the data (you have to find the data you want to change etc).

Essentially, what I am after is a simple 'data entry gui' that would allow generation of data from a form. (e.g. Input 1 = "3.34"). I hope that makes sense. I don't know if this exist, and if it does, I would not have the faintest idea where to start looking?

I was thinking that I could create forms in HTML and convert the data to a csv file via a php script or something to that affect. Seems a bit convoluted though, for something that I think is simple.

I appreciate it is a clumsily worded question - if you need anymore clarification on the question, I will gladly try! :D

Any suggestions would be greatly appreciated.

---

### Post by surfer on 2010-09-01
you could try to write something small with [zenity]("http://freshmeat.net/projects/zenity"). or if you know some python you could do something with [wxPython]("http://www.wxpython.org/") or [glade]("http://glade.gnome.org/"). the latter two versions may be overkill, but are very flexible.

---

### Post by djmac on 2010-09-01
Thanks. Will have a look at those now. Probably more interested in glade and wxpython I think. (Zenity may be a bit simple, but check it out too)

---

### Post by alphacrucis2 on 2010-09-01
> **djmac said:**
> I am not really sure how to word what I am asking. Will give it a go . .. 

I would like to be able to create a data file in something other than gedit. I have made a fortran routine that requires a lot of data. At present you can either type the data manual in the terminal, or manually create a data file in gedit. Both are pretty poor options when you are constantly changing some of the data (you have to find the data you want to change etc).

Essentially, what I am after is a simple 'data entry gui' that would allow generation of data from a form. (e.g. Input 1 = "3.34"). I hope that makes sense. I don't know if this exist, and if it does, I would not have the faintest idea where to start looking?

I was thinking that I could create forms in HTML and convert the data to a csv file via a php script or something to that affect. Seems a bit convoluted though, for something that I think is simple.

I appreciate it is a clumsily worded question - if you need anymore clarification on the question, I will gladly try! :D

Any suggestions would be greatly appreciated.

Open Office Spreadsheet perhaps- maybe using the Open Office built in macro language. Another possibility would be to use the Python scripting language - probably a bigger learning curve and I don't know how to make it work with a gui but you obviously can as many quite complex gui programs are based on python. You may want to ask in the programming section

---

### Post by surfer on 2010-09-01
i like wxPython a lot! never tried glade but seems a nice thing since you can use a graphical editor to create the layout.

---

### Post by djmac on 2010-09-01
> **alphacrucis2 said:**
>  Another possibility would be to use the Python scripting language 

Hmm yes I think this is something I should seriously look into. Thankyou

---

### Post by niteshifter on 2010-09-01
Hi,

OpenOffice Calc can save in CSV format as text. Or ...

OOo with it's internal BASIC language (already mentioned).
OOo with Python (Python-UNO bridge).
OOo with Java (the OfficeBean, specifically). The OOo SDK has an example of this.
... and pull the data you want, then write to a text file for your Fortran routine to process.

Why am I pointing to OOo? You're describing "grid entry" - which is what Calc does and does well. Less re-inventing the wheel ;)

Now, none except the first are quick 'n easy solutions* and may not fit your time constraints but are definitely worth looking at for future needs (i.e. a "general" or template solution).

* To learn the internals of OOo is to learn UNO. Warning: Steep learning curve ahead. But it is very well documented with tons of help available from this and the OOo communities.

---

