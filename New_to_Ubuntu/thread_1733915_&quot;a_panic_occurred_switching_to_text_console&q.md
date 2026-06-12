---
title: "&quot;a panic occurred: switching to text console&quot;"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by rs87424 on 2011-04-19
I am currently using Ubuntu 10.10 and every time my kernel updates I will finish with all of the updates and upgrades and either shutdown or restart my computer. This results in the computer not shutting down and lingers on a black screen with text and at the bottom it says something like "a panic occurred switching to text console" I wait a minute or so but nothing happens.. so I am forced to force shutdown.. which I imagine is not good for the computer so I don't like having to do that... any suggestions on this issue?

---

### Post by mynameisnotbob on 2011-04-19
are the updates installed when you boot it up? Try running this code after the updates instead. ```
sudo shutdown -h now
``` That often fixes hang problems.

---

### Post by ttshivers on 2011-04-19
You might want to try and install updates in the command line by typing this
```
sudo apt-get dist-upgrade
```

And then try restarting by typing this
```
sudo shutdown -r now
```

---

### Post by rs87424 on 2011-04-19
Well the updates and upgrades work fine (mynameisnotbob)

so using the command line to restart or shutdown instead of clicking the shutdown button will prevent this from happening?

I usually use these commands but I didn't think to use them after a kernel upgrade or update.

---

### Post by mynameisnotbob on 2011-04-19
I guess. The -h just helps with hanging issues in general. Since my box is old, I have to use it every time or it hangs.

---

