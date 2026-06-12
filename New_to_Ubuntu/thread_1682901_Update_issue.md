---
title: "Update issue"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by PaulHA2 on 2011-02-06
Hello.

I have an orange triangle with an exclamation mark icon telling me my updates need attention. When I click on "Install updates," my computer flies through downloading 60 updates (which implies it already has those packages downloaded) and then gives me the following message:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

and ```
Failed to fetch http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I'm stuck--how can I fix this? 

Many thanks,

-p.

---

### Post by Daveth on 2011-02-06
if it is this
[HTML]https://launchpad.net/~plaxx/+archive/random-fixes/+index?field.series_filter=[/HTML]

then your ppa looks mal-formed or has changed (it looks like you went to the index file). May be wrong, but try it.

---

### Post by PaulHA2 on 2011-02-06
Yup. That was it. Thanks.

---

### Post by NMALP on 2011-03-23
> **Daveth said:**
> if it is this
[HTML]https://launchpad.net/~plaxx/+archive/random-fixes/+index?field.series_filter=[/HTML]

then your ppa looks mal-formed or has changed (it looks like you went to the index file). May be wrong, but try it.

I have the  same problem I think but cant figure out what to do. I have no clue what a ppa is and am weary about changing anything w/out step by step supervision.


PS I dont have the warning triangle all the time but the update manager still says:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

