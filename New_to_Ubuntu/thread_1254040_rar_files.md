---
title: "rar files"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by flylehe on 2009-08-30
Hi,
I wonder 
1. if lxsplit can extract rar file?
2. where to get source code of unrar since I have to install it without root
3. can unrar joint files named with postfix ".part1.rar" and "part2.rar"?
4. is rar the package to create rar file? where to get its source code?
Thanks and regards!

---

### Post by Bachstelze on 2009-08-30
> **flylehe said:**
> 
1. if lxsplit can extract rar file?

No idea.

> **flylehe said:**
> 2. where to get source code of unrar since I have to install it without root

You can't, but you don't have to be root to use the binary. Alternatively, there is an alternative unrar that is open source, but it can't handle recent versions of the RAR format.

> **flylehe said:**
> 3. can unrar joint files named with postfix ".part1.rar" and "part2.rar"?

Yes.

> **flylehe said:**
> 4. is rar the package to create rar file?

Yes.

> **flylehe said:**
> where to get its source code?

Nowhere.

---

### Post by mangurt on 2009-08-30
You can get unrar by this
```
sudo apt-get install unrar
```
as for the rest of your questions...
yes
yes
yes

---

### Post by flylehe on 2009-08-30
I have to install it without root. So source code please.

---

### Post by Bachstelze on 2009-08-30
> **flylehe said:**
> I have to install it without root. So source code please.

/facepalm

Ask it to RARlab.

---

### Post by flylehe on 2009-08-30
what do you mean? It is not open source?

---

### Post by Bachstelze on 2009-08-30
> **flylehe said:**
> what do you mean? It is not open source?

No it's not.

---

### Post by flylehe on 2009-08-30
In my circumstance, no way to join "x.part1.rar" and "x.part2.rar" then?

---

### Post by Bachstelze on 2009-08-30
Uh-oh, my mistake. It is not free, but it *is* open source. You can get the source [here]("http://archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar-nonfree_3.8.5.orig.tar.gz").

---

### Post by flylehe on 2009-08-30
Thanks!

---

### Post by pedro3005 on 2009-08-30
I believe the 'make install' when installing from source code will fail if you're not root.

---

### Post by Bachstelze on 2009-08-30
> **pedro3005 said:**
> I believe the 'make install' when installing from source code will fail if you're not root.

So? He can just run the compiled binary from his home folder.

---

### Post by flylehe on 2009-08-30
How about rar? Where to get its source code?
Can you tell me where you searched the source code for package?

---

### Post by Bachstelze on 2009-08-30
> **flylehe said:**
> How about rar? Where to get its source code?

rar is *really* not open source. But it doesn't really matter, you can just run the binary from your home folder.

> **flylehe said:**
> Can you tell me where you searched the source code for package?

[http://packages.ubuntu.com](http://packages.ubuntu.com) - search for your package, and download the .orig.tar.gz archive from the left panel, or just go to the developer's website. ;)

---

### Post by flylehe on 2009-08-30
where do you get rar binary? My computer doesn't have one.

---

### Post by Bachstelze on 2009-08-31
> **flylehe said:**
> where do you get rar binary? My computer doesn't have one.

[http://www.rarlab.com/download.htm](http://www.rarlab.com/download.htm)

---

