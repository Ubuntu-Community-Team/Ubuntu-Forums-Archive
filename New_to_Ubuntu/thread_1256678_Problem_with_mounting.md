---
title: "Problem with mounting"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Zopiac on 2009-09-02
Here's the deal. I have to:
1. Mount an .iso to a given diretory
2. Run a file off of mounted .iso
3. Mount a different .iso to the same directory
4. Have the other file continue using the contents on the second .iso
5. Mount the first .iso back on the same directory for it to finish working.

However, I am having this problem:

```

$ sudo mount /file.iso /mount/ -o loop
$ sudo mount /file2.iso /mount/ -o loop
$ sudo mount /file.iso /mount/ -o loop
mount: according to mtab /file.iso is already mounted on /mount/ as loop

```

How do I get /file.iso to mount back on /mount/ after I have gotten /file2.iso mounted there? When I try 'sudo umount /file2.iso' it tells me that it is not mounted...

---

### Post by 3rdalbum on 2009-09-02
Common mistake. You need to unmount the mount point, not the ISO file:

```
sudo umount /mount
```

---

### Post by Zopiac on 2009-09-02
> **3rdalbum said:**
> Common mistake. You need to unmount the mount point, not the ISO file:

```
sudo umount /mount
```

Weelll...

```

$ sudo umount /mount/
$ sudo mount /file.iso /mount/ -o loop
mount: according to mtab /file.iso is already mounted on /mount/ as loop

```

---

### Post by jrox717 on 2009-09-03
>  mount: according to mtab /file.iso is already mounted on /mount/ as loop 
Well, is /file.iso still mounted? I'm not sure how mounting multiple isos to a single directory works, but before you unmount file2, are both mounted there? If so, then I might guess that 
```
 umount /mount/ 
```
only unmounts the last iso you mounted. What happens if you issue that command again?

---

### Post by Zopiac on 2009-09-03
> **jrox717 said:**
> Well, is /file.iso still mounted? I'm not sure how mounting multiple isos to a single directory works, but before you unmount file2, are both mounted there? If so, then I might guess that 
```
 umount /mount/ 
```
only unmounts the last iso you mounted. What happens if you issue that command again?

That makes sense, and it seems to have worked! Umount probably sees something like: "mount_on_[dir], [dir]=/mount/"=1 even though there are multiple mounts, it just sees the bottom entry for /mount/ in mtab. Even though you umount the last entry, theres still another there to umount. The error telling me that /file1.iso is still mounted probably looks for /file.iso mounted somewhere in mtab, instead of /mount to be mounted.

Also, even though you mounted over another mount, which erases the other mount, it doesn't properly unmount the other mount. Hence the need for umount in these cases.

I'm finally understanding bits of how Linux works :)

---

