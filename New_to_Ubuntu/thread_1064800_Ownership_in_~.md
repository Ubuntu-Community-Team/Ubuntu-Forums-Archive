---
title: "Ownership in ~"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by HavocXphere on 2009-02-09
[SOLVED]

I've got some rogue files in my home directory that I want to take ownership of. Can I safely recursively hit everything in home with a chown or are there some files that must have other(root?) ownership.

i.e.
```
sudo chown -R havoc:havoc /home/havoc/
```

Thanks

---

### Post by drs305 on 2009-02-09
Normally everything in your $HOME directory should be owned by you. You can run a quick check to see if *root* owns anything with the following command. Once you have investigated and are satisfied with the results, you can run the command you posted.
```

cd $HOME && pwd && ls -la -R | grep "root"

```

---

### Post by HavocXphere on 2009-02-09
Cool.

I've checked with the command you provided - quite a few files are root owned...must be from back when I did the "sudo vs kdesudo" thing wrong.

Thanks

Edit: Permissions fixed. :)

---

