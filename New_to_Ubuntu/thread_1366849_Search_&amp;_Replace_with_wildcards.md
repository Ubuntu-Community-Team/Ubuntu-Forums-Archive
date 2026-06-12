---
title: "Search &amp; Replace with wildcards?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by gspawn69 on 2009-12-28
Hi there,

I have a text file that has page numbers in it that I want to remove. The standard search & replace won't work though because the page number keeps incrementing, and the search & replace function doesn't accept wildcards that I can see. So, what I'm wondering is, how can I have all these page numbers removed automatically so I don't have to go deleting them one at a time?

The page numbers look like this:

(1 of 465)28-7-2007 14:15:45
(2 of 465)28-7-2007 14:15:45

etc...

---

### Post by Temposs on 2009-12-28
OK. So open your file in Open Office. Press Ctrl-F to bring up Find/Replace. Click on "More Options" and check "Regular expressions". In the Find field, put this:

```
\(.* of 465\)
```

Put nothing in the replace field. Click "Replace All" and it should get rid of all your page number things.

---

### Post by andrew.46 on 2009-12-29
Hi gspawn,

> **gspawn69 said:**
> I have a text file that has page numbers in it that I want to remove. The standard search & replace won't work though because the page number keeps incrementing, and the search & replace function doesn't accept wildcards that I can see. 

sed will get you started with this one. Try the following in a terminal:

```
echo '(1 of 465)28-7-2007 14:15:45' | sed 's/(.*)//g'
```

and if this close to what you are after you could then run the command on your file:

```
sed -i_bak 's/(.*)//g' myfile
```

Bear in mind that this command will change your original file's contents with no prompting although it incorporates the creation of a backup file.

Andrew

---

### Post by gspawn69 on 2009-12-29
That worked great thanks!

---

### Post by glubbdrubb on 2009-12-29
If it works out then just mark this thread as solved please, using the "Thread Tools" at the top of the page.

Thanks

---

