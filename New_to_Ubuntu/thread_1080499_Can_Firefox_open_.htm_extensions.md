---
title: "Can Firefox open .htm extensions?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by suomalainen on 2009-02-25
Ubunteros,

Can Firefox 3.0.6 (Ubuntu 8.04LTS) open files with .htm extension?

I got a web site loaded on my web server. I can open it with Explorer, Opera and Safari. flawlessly.

However, when I use Firefox for either XP or Ubuntu 8.04LTS I only get a message that says:

You have chosen to open:

index.htm

Which is a html document

What should Firefox do with this file:

Open with: (here you use program to open file)
Save File:

Any insight into this problem would be greatly appreciated.

Thank You!

---

### Post by billgoldberg on 2009-02-25
I'll try it.

--

Yes it works, I quickly created a html page and saved it a test.htm

then double clicked it and firefox opened it without problems.

--

Save this a xxx.htm

and see if firefox will open it:

```
<html>
<head>
<title> test </title>
</head>
<body>

<p><h1>test</h1></p>

</body>
</html>

```

Does that give you errors?

--

Why don't you just use .html? .htm is so 1999.

---

### Post by suomalainen on 2009-02-25
thanks billgoldberg!

I think we need to focus on my very first post. This being that the pages are already on the server. As I mentioned, I can open them right from the web server using Explorer, Opera and Safari. Only Firefox does not want to open them instantaneously!

Instead, Firefox only wants to download to desktop. And yes once on desktop I can double click and page opens.

I want Firefox to instantly open the URL.!

Does this help?

---

### Post by llamabr on 2009-02-25
Post the url so we can test this behavior.

---

### Post by billgoldberg on 2009-02-25
Your best bet would be to ask around on the Firefox forums or bugzilla.

---

### Post by llamabr on 2009-02-25
Also, as an afterthought, when you have the option to open with or save as, search through open with until you open with firefox.  Mine is in:

brock@vader:~/rdata$ which firefox
/usr/bin/firefox
brock@vader:~/rdata$ 

See if telling it to open with firefox fixes your problem.  I'm a bit skeptical, but worth a try.

---

### Post by suomalainen on 2009-02-25
llamabr,

You said:

"search through open with until you open with firefox."

You are 100% correct this is what I want Firefox to ask me. BUT it doesn't. It only gives me option to save the file to desktop or to cancel.

Is there a way to force Firefox to give me the OPEN WITH option?

Thanks!

---

### Post by llamabr on 2009-02-25
Strange.  Mine doesn't ask me about htm, it just opens.  Can you open this one:

[http://www.1stheadlines.com/xbox.htm](http://www.1stheadlines.com/xbox.htm)

What's the url you're having trouble with?

---

### Post by suomalainen on 2009-02-25
OK. I went to the folder and renamed index.htm to index.html

When I entered the url into the browser Firefox now opened this page!!!

When I click on a link within the page Firefox complains that:

You have chosen to open
page 001.htm
Which is an HTML document.

Would you like to save this file?

CANCEL or SAVE FILE

There has to be a way to force Firefox to open htm files automatically?

---

