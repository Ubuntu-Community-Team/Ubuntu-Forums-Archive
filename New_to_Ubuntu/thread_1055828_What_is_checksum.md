---
title: "What is checksum?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by BuntuFirstTimer on 2009-01-31
I use Brasero disk burner. However, I don't know what does checksum contribute to the function.

Any ideas?

---

### Post by zvacet on 2009-01-31
[Here]("https://help.ubuntu.com/community/Checksum") and [here.]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by BuntuFirstTimer on 2009-01-31
I don't know how to comprehend what does it do exactly.

What if somebody doesn't do checksum when burning a disk. What is the consequence?

---

### Post by niteshifter on 2009-01-31
Hi,
> **BuntuFirstTimer said:**
> I don't know how to comprehend what does it do exactly.

What if somebody doesn't do checksum when burning a disk. What is the consequence?

A checksum process (like md5sum, for example) calculates a unique value (the checksum) for a chunk of data. Every time the process runs - on the same data - the same checksum will be produced.

Change any bit of that data and apply the checksum process again you'll get a different checksum value. Hence the usefulness of "checksumming" - to see if any changes in a parcel of data have occurred.

I'll start to answer your second question with a question: Without a checksum value how could you tell that the parcel of data you received is correct?

If that parcel was a human-readable message - and a short one - you could just study it to see if there are any errors in it. But what about "computer data"? Such stuff makes no sense to us people (at least without at lot of experience in reading computer "codes"). What about a parcel of information like a full CD or DVD? It would take a long time to find the error(s) by inspecting it.

So, the consequence of not having a checksum value is not knowing if what you have received is correct: A true copy, bit for bit, of what the originator produced.

---

