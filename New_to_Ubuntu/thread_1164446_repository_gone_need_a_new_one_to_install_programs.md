---
title: "repository gone need a new one to install programs on server"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by mishkin on 2009-05-19
First off this is debian etch... but I'm on my ubuntu laptop and not regged at debian forums so I thought I'd ask here

I had these:

deb [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) etch main non-free

deb-src [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) etch main non-free

but they no longer work so I can't install several programs I need...

setting up a torrent server done it many times before it's ussually straightforward (but I am a linux nub)

I found what I thought was a good replacement but it went  on and on about a public key not being found and I had no idea how to do that either (my old ones didn't need a key)

HELP 
:)

---

### Post by Didius Falco on 2009-05-19
Hi,

If you go to the website of the alternate you found, they should have a GPG key available for download along with instructions on how to add it to your sources keys.


Regards,

Didius

---

### Post by mishkin on 2009-05-19
yeah said subsitute's method of getting the key starts with apt-get install (something) .. which it says said package doesn't exists so still stuck

could someone find me some replacement urls and post them here

and maybee the key download link>?>>?

I said i could do this if they went linux seedbox and now I feel terrible cause it's sitting idel and I"m looking stupid :(

(plus I'm gonna need the change for when I reinstall with ssd drives in my box)

---

### Post by mishkin on 2009-05-19
found the answer myself.... no key needed

added this one and all programs installed fine

deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) etch main non-free

---

