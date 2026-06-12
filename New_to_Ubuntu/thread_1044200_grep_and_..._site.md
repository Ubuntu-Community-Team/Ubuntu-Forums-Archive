---
title: "grep and ... site"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by helphope on 2009-01-19
I use grep with txt files, but I was wondering if there is a way to apply it to a site.
Instead of 

> grep -i apple fruitlist.txt

can I write something like

> grep -i apple [http://name_of_the:site.eu](http://name_of_the:site.eu) >output.txt?

What I can do with google I'd like to do it with grep.

> site: [http://en.wikipedia.org](http://en.wikipedia.org) "grep"



Or is there a way to get some particular text from a site working from the command line?

:confused:
Thanks

---

### Post by yeats on 2009-01-19
I'm not sure what your specific needs are here, because it sounds like Google (and other search engines) would be best, but if you want to search the HTML of a site with grep, you would have to download the page with wget

```
wget [*URL*]
```

then grep from there like you would with any text file.

Is that helpful?

---

### Post by helphope on 2009-01-19
Thanks for replying. I tried this:
```
wget [*URL*]| grep word_to_search >output.txt
```

but that does not work. I think because grep doesn't work with html files.

---

### Post by emarkd on 2009-01-19
html is just text, so grep will work fine.  try:

```
wget -q -O- http://www.whatever.com | grep sometext
```

The -q will tell wget to be quiet and the O sends the output to stdout

---

### Post by snova on 2009-01-19
> **helphope said:**
> Thanks for replying. I tried this:
```
wget [*URL*]| grep word_to_search >output.txt
```

but that does not work. I think because grep doesn't work with html files.

grep will work with anything you give it. You could even feed it binary files (though its output wouldn't be as readable).

wget simply doesn't write the downloaded page to stdout.

---

### Post by unutbu on 2009-01-19
To cut down on the amount of html code tags, you can convert the html to a plain text file before you grep too:
```

sudo apt-get install html2text
wget "URL" -O- | html2text -nobs | grep KEYWORD
```

Note that some URLs contain ampersands (&), in which case you need to protect the URL from the shell interpreter by enclosing it in quotations.

---

### Post by helphope on 2009-01-20
Thanks everybody for answering. 

```


wget "URL" -O- | html2text -nobs | grep KEYWORD
```

This one works greatly.
Thanks again

---

### Post by Stefanie on 2009-01-20
i use w3m to do this: 

```
w3m www.ubuntu.com -dump | grep Ubuntu
```

the option "-dump" is used to send the output to stdout. "| grep" pipes stdout to grep. 

to install w3m:

```
sudo apt-get install w3m
```

---

### Post by unutbu on 2009-01-20
Thanks Stefanie, I didn't know about w3m until now... and it looks great! :)

---

