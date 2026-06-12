---
title: "Launcher Scripts"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by Jademalo on 2011-04-06
So I used to have some nice launchers set up to run my minecraft server, then my HDD died and I lost them, and cant for the life of me remember them.

Just running "java -jar -Xmx2048 \home\scotty\MinecraftServer\CraftBukkit.jar" doesnt place all of the server files in the right place for some reason, So I used to have something set up.

It was all one like, and SOMETHING like:

'bash "cd \home\scotty\MinecraftServer\" && "java -jar -Xmx2048 \home\scotty\MinecraftServer\CraftBukkit.jar"'

But.. that doesnt work. Something is wrong, and I cant figure out what.

Any help would be appreciated, thanks!

---

### Post by sisco311 on 2011-04-06
Use forward slashes `/' instead of backslashes `\': 

```
bash -c "cd /home/scotty/MinecraftServer/ && java -jar -Xmx2048 ./CraftBukkit.jar"
```

---

### Post by Jademalo on 2011-04-06
> **sisco311 said:**
> Use forward slashes `/' instead of backslashes `\': 

```
bash -c "cd /home/scotty/MinecraftServer/ && java -jar -Xmx2048 ./CraftBukkit.jar"
```

Perfect!
Thank you so much!
=]

---

### Post by sisco311 on 2011-04-06
You're welcome!

---

