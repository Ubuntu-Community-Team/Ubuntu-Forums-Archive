---
title: "deleting Vista?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by volkanmet86 on 2009-06-02
i have installed ubuntu to the same partition where vista exists. now i like to use ubuntu only. how can i erase vista without giving any harm to ubuntu?

---

### Post by neo.patrix on 2009-06-02
I am sorry to say but your question is not very clear to offer a solution, need more information

1) what do you mean by deleting vista? just getting rid of your C: drive (assuming you have vista on it) or cleaning up your entire HD of other NTFS partitions as well

2) Are you using LiveCD, Wubi or have you already installed Ubuntu?

---

### Post by Mark Phelps on 2009-06-02
You can follow the directions in the link below to "move" your Ubuntu installation outside of Vista into its own partition:

[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by MichaelSammels on 2009-06-02
Or if you simply wish to delete the partition boot to the Ubuntu LiveCD and run GParted to delete the Vista Partition, and extend the Ext3 one.

---

### Post by mal1958 on 2009-06-02
> **MichaelSammels said:**
> Or if you simply wish to delete the partition boot to the Ubuntu LiveCD and run GParted to delete the Vista Partition, and extend the Ext3 one.

This may not work if they istalled in the **same** partition that Vista is in.

Mike

---

### Post by volkanmet86 on 2009-06-02
i have installed vista to the c: driver and i installed ubuntu to the same c: driver. now i like to remove, delete or erase vista from my c: drive

---

### Post by Cypher on 2009-06-02
You will have to better explain how you did the installation. Did you install Ubuntu while you were already in Windows? This is the WUBI method. Or did you burn a CD with the LiveCD of Ubuntu, boot from it and then within the Gnome desktop, choose the Install option on the desktop and install Ubuntu?

There's a BIG difference in what the correct course of action to remove Windows based on how you installed it.

If you installed through the LiveCD, then just by the fact that you installed to the same partition as Windows (hopefully re-formating it to EXT3), you've already blown Windows away. If you can still boot into Windows, then you must have installed using WUBI and there are numerous links about removing Windows and keeping Ubuntu on Google...

---

### Post by mal1958 on 2009-06-02
> **volkanmet86 said:**
> i have installed vista to the c: driver and i installed ubuntu to the same c: driver. now i like to remove, delete or erase vista from my c: drive

To further our information here:

Did you:


[LIST=1]
[*]install to dual boot giving Ubuntu it's own partition on C: drive?
[*]Install in windows so there is an icon on the Windows desktop for Ubuntu?
[*]or How 'Exactly' did you install it?
[/LIST]

  If '1' then MichaelSammels suggestion will probably work. 

  If '2' then I don't think you can erase Vista from your system in a simple manner.

Please elaborate...

  (EDIT):  OK, scratch the above.   I didn't know there were ways to save Linux and rid youtself of Vista if method '2' was used (IE  the Wubi way).

Mike



Mike

---

### Post by neo.patrix on 2009-06-02
> **Mark Phelps said:**
> You can follow the directions in the link below to "move" your Ubuntu installation outside of Vista into its own partition:

[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

Suggests an appropriate solution

Or 

If that is too complex, you can do a fresh installion using LiveCD. Delete your C: drive and whatever amount of memory is freed use it for making Ubuntu Partitions and system installation. But cannot help much without knowing how your hard-disk might be partitioned. How your data is placed etc...

---

### Post by volkanmet86 on 2009-06-02
> **Cypher said:**
> You will have to better explain how you did the installation. Did you install Ubuntu while you were already in Windows? This is the WUBI method. Or did you burn a CD with the LiveCD of Ubuntu, boot from it and then within the Gnome desktop, choose the Install option on the desktop and install Ubuntu?

There's a BIG difference in what the correct course of action to remove Windows based on how you installed it.

If you installed through the LiveCD, then just by the fact that you installed to the same partition as Windows (hopefully re-formating it to EXT3), you've already blown Windows away. If you can still boot into Windows, then you must have installed using WUBI and there are numerous links about removing Windows and keeping Ubuntu on Google...

i think i used the wubi method. i was using vista when i installed ubuntu. i put the ubuntu cd while the vista was operating and i can chose between ubuntu and vista just after i turn on the pc. the problem is the both ubuntu and vista are in the c: drive

---

### Post by LewRockwell on 2009-06-02
as long as you have saved/backed-up all your valuable data off-machine, the quickest way would be to just reformat, repartition, and re-install.

those procedures are covered elsewhere on this, and other, forums and are outside of the scope of this post, given you are the only one who knows exactly what your needs/necessities are.

---

