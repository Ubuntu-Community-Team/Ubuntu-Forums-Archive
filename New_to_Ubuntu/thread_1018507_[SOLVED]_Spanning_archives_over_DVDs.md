---
title: "[SOLVED] Spanning archives over DVDs"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-12-22
A basic question, perhaps, but one that I've not managed to find the answer to.

When I create a very large archive (e.g. tar.bz2), how can I span this over several DVDs? I want to make the backup, but I don't know how to split the archive into DVD-bite sizes.

---

### Post by scorp123 on 2008-12-22
> **Paddy Landau said:**
> When I create a very large archive (e.g. tar.bz2), how can I span this over several DVDs? I don't recommend that ... If you lose one DVD or if it gets damaged somehow, then your backup is lost.

But to answer the question ... someone already wrote a good tutorial here:
[http://www.base64.co.uk/splitting-large-files/](http://www.base64.co.uk/splitting-large-files/)

He's using 100M as base size because he wants his stuff to fit onto 100M ZIP disks. So you'd have to adjust that to 4GB. 

Please keep this one in mind: A DVD only has room for ~4.3 Gigs ... not 4.7G! Read here why:
[http://ubuntuforums.org/showthread.php?p=6207168#post6207168](http://ubuntuforums.org/showthread.php?p=6207168#post6207168)

My advice would be to aim for a size of 3.9 Gigs per archive (you'd lose about 200 MB space per DVD disk ... and that's not much). If you ever plan to use those archives on a non-UNIX-like OS such as Windows-something then it could be that you will run into problems if you try to unpack your files there: depending on the filesystem and the version of Windows used it could be that there is a maximum filesize limit of 4 GB. Files bigger than that cannot be read. So if compatibility with older Windows versions matters to you then you should try to stay under the 4 GB limit. On the other hand if it does not matter to you ... oh well then: in that case you could aim for a filesize of 4.2 ~ 4.3 GB per archive file. Please keep in mind that you only have room for 4482 MB (= 4.37 GB) per DVD layer.

---

### Post by Paddy Landau on 2008-12-22
> **scorp123 said:**
> I don't recommend that ... If you lose one DVD or if it gets damaged somehow, then your backup is lost.
The backup is for convenience; I have another off-site backup.

Thanks for the link to the tutorial; it answers my question. I had read the tar manual, but clearly I hadn't understood it properly.

Thanks too for the caveats about compatibility (I only use Ubuntu and, occasionally, Windows Vista, so that's not a problem for me).

Thanks, too, for the explanation of the sizes. That saves me some confusion!

---

### Post by Paddy Landau on 2008-12-23
Hmm...

I followed the instructions for a script to automate spanning in
[http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#SEC156](http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#SEC156)

I rewrote it in bash, as I understand bash but not sh. And it doesn't work.

I've posted my question here:
[http://ubuntuforums.org/showthread.php?t=1019633](http://ubuntuforums.org/showthread.php?t=1019633)

Edit: Problem solved. It was my misunderstanding that caused it.

---

