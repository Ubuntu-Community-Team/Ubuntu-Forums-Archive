---
title: "Bit Torrent HD Issue"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Diametric on 2010-02-01
I attempted to downlad a large torrent the other day and was only successful in getting about 25Mb of a file over 2 Gb is size.  Back in Windows days, I'd need to defrag after a couple of failed torrent downloads.  Do I need to do that in Ubuntu?  If so, by what measure can one tell if there is a need or not.
 
Cheers!

---

### Post by switch10 on 2010-02-01
> **Diametric said:**
> I attempted to downlad a large torrent the other day and was only successful in getting about 25Mb of a file over 2 Gb is size.  Back in Windows days, I'd need to defrag after a couple of failed torrent downloads.  Do I need to do that in Ubuntu?  If so, by what measure can one tell if there is a need or not.
 
Cheers!

Hi,
you wont need to defrag ext filesystems, like you do NTFS.  What is the error message you are getting from your torrent client?  What torrent client are you using?

---

### Post by Diametric on 2010-02-02
Thanks for your reply!  There is no error message with the torrent, the seeder closed the connection.  My concern is specifically with the HD - having downloaded the 25Mb and hypothetically more like it - is my HD going to get trashed?  If so, how would i tell?  I guess where I'm coming from is if I got 25Mb on my HD from a failed torrent DL, where is it and how do i get rid of it to free up space.  I bet I'm just gun shy from MS, but would like to make certain.

---

### Post by NickJones on 2010-02-02
It sounds more like a problem at the seeders end, try another torrent and see if the problem persists.
Nick

---

### Post by Diametric on 2010-02-02
Thanks for the reply, but again, I am not attempting to troubleshoot a torrent issue.  I am trying to get an expalanation as to where, if at all the partial download goes.  Is it on my HD?  If it is, is it cluttering it up?  How would I tell...etc?  Thanks all!

---

### Post by J V on 2010-02-02
What do you do in windows to delete the data:

[LIST=1]
[*]Open torrent program
[*]Click the torrent
[*]Press delete button
[/LIST]

What do you do in ubuntu to delete the data:

[LIST=1]
[*]Open torrent program
[*]Click the torrent
[*]Press delete button
[/LIST]

...

---

### Post by electricFan on 2010-02-02
> **J V said:**
> What do you do in windows to delete the data:

[LIST=1]
[*]Open torrent program
[*]Click the torrent
[*]Press delete button
[/LIST]

What do you do in ubuntu to delete the data:

[LIST=1]
[*]Open torrent program
[*]Click the torrent
[*]Press delete button
[/LIST]

...

Yeah that's probably your best bet.  Once you delete it it should be gone, no more worries.

---

### Post by niffcreature on 2010-02-02
just to mention:
i am pretty sure defragging on any system doesnt actually help any performance.
what it does is make the data more easily recoverable if something were to happen with the hdd

---

### Post by thatguruguy on 2010-02-02
> **niffcreature said:**
> just to mention:
i am pretty sure defragging on any system doesnt actually help any performance.
what it does is make the data more easily recoverable if something were to happen with the hdd

You're wrong about that, actually. Defragging in windows not only puts the files back together when possible (as opposed to being scattered around the hard drive), it also moves everything to the front of the drive, where it is accessed faster.

---

### Post by Diametric on 2010-02-02
> **thatguruguy said:**
> You're wrong about that, actually. Defragging in windows not only puts the files back together when possible (as opposed to being scattered around the hard drive), it also moves everything to the front of the drive, where it is accessed faster.
 
That's what I thought.  And, it is also my impression that the way ext4 is managed is that you don't "need" to defreg, but I was concerned that the failed downloads could clutter my HD.

---

### Post by mkvnmtr on 2010-02-02
Everything I have read form experienced linuw users has said that defragmentation is not  required or advisable. I have also seen some speed tests that seem to show that no speed is gained. That being said I was under the impression that when you started a 2 GB torrent that 2Gb was mappd off on the hard drive. Not 25 Mb that you have downloaded. The reason for this belief is that you have not downloaded the first 25Mb. Yu have downloaded random bits of the whole 2Gb. Rhus when you complete the torrent everything is in the place orginaly mapped out. Ithink that is how it works but I could be wrong.

---

### Post by qyot27 on 2010-02-02
Most BitTorrent clients download the data to the end file, unless you have it set to copy to a specific location after it's done.  If you delete the file, the data is gone - it doesn't leave remnants.  This is true no matter what filesystem you use.  Fragmentation has more to do with free space and where data is allocated, but if you delete a file, then those fragments clear.  The problem is when, as with NTFS and FAT, that there isn't a caching or supervisory system in place to make sure the files are contiguous, which inevitably leads to files being broken up into disparate data chunks and shoved into any place they'll fit, creating fragmentation.  To my knowledge, *all* of the ext filesystems, not just ext4, are fragmentation-resistant.  Doesn't mean that freak fragmentation can't occur (or very, incredibly slowly over long periods of time) but it's generally something you don't have to worry about.  Ext4's extent support and delayed allocation features far further reduce the chance of fragmentation occurring over the previous two ext filesystems, though.

But either way, this can also be somewhat avoided (even on Windows systems) by using the Full Allocation option that most clients have.  It makes sure that all the data for the torrent is allocated before it begins downloading, so that fragmentation is kept to a minimum.  As a general rule, if you're going to be downloading torrents, use Full Allocation.

[quote=mkvnmtr]That being said I was under the impression that when you started a 2 GB torrent that 2Gb was mappd off on the hard drive. Not 25 Mb that you have downloaded. The reason for this belief is that you have not downloaded the first 25Mb. Yu have downloaded random bits of the whole 2Gb. Rhus when you complete the torrent everything is in the place orginaly mapped out. Ithink that is how it works but I could be wrong.[/quote]
No, by default most torrent clients do not work that way, at least on Windows - the default is to do sparse allocation, which can fragment very heavily, and it does not allocate all 2GB when the file has started downloading.  However, that's simply the default - most clients do have the option to pre-allocate all the space they need, but obviously there are a lot of people that refrain from using it, whether because they just use the defaults or they don't like the idea.

---

### Post by Diametric on 2010-02-02
> **qyot27 said:**
> Most BitTorrent clients download the data to the end file, unless you have it set to copy to a specific location after it's done. If you delete the file, the data is gone - it doesn't leave remnants. This is true no matter what filesystem you use. Fragmentation has more to do with free space and where data is allocated, but if you delete a file, then those fragments clear. The problem is when, as with NTFS and FAT, that there isn't a caching or supervisory system in place to make sure the files are contiguous, which inevitably leads to files being broken up into disparate data chunks and shoved into any place they'll fit, creating fragmentation. To my knowledge, *all* of the ext filesystems, not just ext4, are fragmentation-resistant. Doesn't mean that freak fragmentation can't occur (or very, incredibly slowly over long periods of time) but it's generally something you don't have to worry about. Ext4's extent support and delayed allocation features far further reduce the chance of fragmentation occurring over the previous two ext filesystems, though.
 
But either way, this can also be somewhat avoided (even on Windows systems) by using the Full Allocation option that most clients have. It makes sure that all the data for the torrent is allocated before it begins downloading, so that fragmentation is kept to a minimum. As a general rule, if you're going to be downloading torrents, use Full Allocation.
 
 
No, by default most torrent clients do not work that way, at least on Windows - the default is to do sparse allocation, which can fragment very heavily, and it does not allocate all 2GB when the file has started downloading. However, that's simply the default - most clients do have the option to pre-allocate all the space they need, but obviously there are a lot of people that refrain from using it, whether because they just use the defaults or they don't like the idea.
 
Thank you...that's what I was looking for.  I appreciate the reply.

---

