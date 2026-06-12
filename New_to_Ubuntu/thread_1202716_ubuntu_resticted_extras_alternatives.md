---
title: "ubuntu resticted extras alternatives"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-02
are there any alternatives in a whole package like restricted?

---

### Post by LowSky on 2009-07-02
Could you please elaborate a bit more. What exactly are you looking for?

Technically you could installed the ubuntu-restricted-extras packages all seperatly if you dont need all of them

---

### Post by .Maleficus. on 2009-07-02
Fluendo codecs.  [You can buy them here]("http://shop.canonical.com/product_info.php?products_id=244").

---

### Post by Ji Ruo on 2009-07-03
What is the issue that you have with the restricted extras package? 

Everything in there should be totally above board and legal to download. The reason they aren't included comes down to ideology - ubuntu is basically about making software and formats free, so these proprietary formats aren't included by default.

The only grey area in terms of legality is the libdvdcss2 package from the medibuntu repositories. This won't be included in the restricted extras package, it has to be downloaded separately. If you want dvd playback and you want to make sure that what you're doing is totally above board, purchase the fluendo package with mpeg2 support from the canonical store (under the software section). Or, get the powerdvd package (also from canonical store) and install the restricted extras package for the other proprietary formats that you'll need.

---

### Post by philinux on 2009-07-03
> **heyyy said:**
> are there any alternatives in a whole package like restricted?

Have a look to find out which bit you need rather than the whole lot.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by .Maleficus. on 2009-07-03
> **Ji Ruo said:**
> Everything in there should be totally above board and legal to download. The reason they aren't included comes down to ideology - ubuntu is basically about making software and formats free, so these proprietary formats aren't included by default.
I don't know about the legality of the included software in Australia, but Canonical certainly cannot distribute the codecs in the USA.  It definitely is a legal issue.  Linux Mint (an Ubuntu based distro) offers two versions of their releases for this very reason.
[quote=Linux Mint Download Page]Universal Edition
This edition aims to provide the same features as the Main Edition without including proprietary software, patented technologies or support for restricted formats. If you're a magazine, a reseller or a distributor in Japan or in the USA then choose this edition.[/quote]

---

### Post by Ji Ruo on 2009-07-03
> **.Maleficus. said:**
> I don't know about the legality of the included software in Australia, but Canonical certainly cannot distribute the codecs in the USA.  It definitely is a legal issue.  Linux Mint (an Ubuntu based distro) offers two versions of their releases for this very reason.

Canonical doesn't distribute the codecs in Australia with the install cd and I doubt they want to, because ubuntu is all about the ideal of free and accessible software. They do provide access to, and support for the restricted extras package though as an individual download. The only exception is the libdvdcss2 package from the medibuntu repository, this is not maintained by Canonical but can be obtained from the unofficial ubuntu community. This is for the playback of region encoded dvds.

I think you will find that this is the same issue with linux mint offering two different editions. The one available in the US is the equivalent of the standard ubuntu package, and the other edition is provided outside the US because the mint distro does not have an underlying ethos of 'free software for all' that ubuntu has.

If the situation with canonical in the US is different, they must have a different website for the US, and you must not be able to download the restricted extras package from the canonical-maintained repositories. If you or someone else would be willing to cut and paste the relevant sections/terminal output to show that this is the case I'd appreciate it.

---

### Post by .Maleficus. on 2009-07-04
Um, Canonical isn't a US company.  They're Scottish (Irish?  They're in Great Britain) so US laws do not apply to them.  They can distribute what they want but people in the US have to know that if they download it, it is illegal because Canonical didn't pay royalties to the codecs makers.  Thus, the non-free codecs cannot be distributed on free software.

---

### Post by Ji Ruo on 2009-07-05
Copyright law is very complicated and there are plenty of ongoing disputes over who owns what at present. That's my conclusion after some more browsing on the matter.

The ubuntu community documentation has been updated since I last used ubuntu (just installed kubuntu last week after using Vista for a few months).

[FreeFormats - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FreeFormats")

The post by Love Young here is also helpful -

[RestrictedFormats/Talk]("https://help.ubuntu.com/community/RestrictedFormats/Talk")


I was surprised to see that there is actually no problem with using libdvdcss2 on your pc under the DMCA (the applicable US law). Carlos Arenas (author of the 1st link) does mention problems with using the .mp3 format but after reading about the lawsuits I can see that these are not going to affect personal use. All of the lawsuits are regarding the distributors, such as Microsoft, rather than the end user. Streaming .mp3s over a network may be a different story.

Java is licensed and you have to agree with that license when it's installed. And the flash on restricted-extras comes straight from the company. I don't know what else there is in the restricted extras package that would break the law, if anyone knows then please post...

The conclusion I've come to is that the restricted-extras package is legal for personal use in the US, and as a rule of thumb would be legal in most countries (maybe even all!) for personal use. If you are a business or organisation setting up a network, perhaps pay for an hour's time with a specialist (a lawyer who works in copyright).

---

