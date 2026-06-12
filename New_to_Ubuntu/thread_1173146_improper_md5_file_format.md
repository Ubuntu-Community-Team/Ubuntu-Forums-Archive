---
title: "improper md5 file format"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by egalvan on 2009-05-29
I downloaded the md5 file for 9.04, but it gives this error...

```
 md5sum: 9.04.md5: no properly formatted MD5 checksum lines found

```


this is the file...

```
3b5e9861910463374bb0d4ba9025bbb1 *ubuntu-9.04-alternate-amd64.iso
c564ae16dffb51a922aef74a07250473 *ubuntu-9.04-alternate-i386.iso
cace6ea9dde8dc158174e345aabe3fae *ubuntu-9.04-desktop-amd64.iso
66fa77789c7b8ff63130e5d5a272d67b *ubuntu-9.04-desktop-i386.iso
8f921e001aebc3e98e8e8e7d29ee1dd4 *ubuntu-9.04-netbook-remix-i386.img
78cf52114804f80576b0bfc8f5984339 *ubuntu-9.04-server-amd64.iso
20480057590ff8b80ad9094f40698030 *ubuntu-9.04-server-i386.iso
5e6f6acf2105c366db2f9727e2a65d03 *wubi.exe

```


I've tried:
...removing the "*" and using spaces (from one to seven),
...using tabs (from one to four),
all fail.

I am using gedit for the changes.

What am I doing wrong?

---

### Post by Hospadar on 2009-05-29
I don't know why you're getting that error, those are formatted correctly.

You could always just try md5-ing the iso's you want to check and then diffing the sums by hand

---

### Post by egalvan on 2009-05-29
> **Hospadar said:**
> ,,,those are formatted correctly.

...try md5-ing the iso's you want to check and then diffing the sums by hand

OK, I used md5 on the files, and the checksums aren't even close...

I think I have a wrong file...
maybe they are a different type.

More study time...

Thanks.

---

