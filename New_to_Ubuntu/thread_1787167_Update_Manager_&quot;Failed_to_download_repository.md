---
title: "Update Manager: &quot;Failed to download repository information&quot;"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by hopefulkayaker on 2011-06-20
On my desktop, I see a red triangle with an exclamation mark in it, next to the date at the top of my screen. Double-clicking on it brings up the update manager, which displays the following message:

"**Software updates may be available for your computer. **The package information was last updated 11 days ago. Press the 'Check' button below to check for new software updates."

After pressing the 'Check' button, a window appears with the title "Updating Cache". The another window appears in its place, saying:

"**Failed to download repository information **Check your internet connection." 

There's a details field which says:

```
W:Failed to fetch http://skulltag.net/download/files/release/deb/dists/stable/multiverse/source/Sources  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I have had no trouble with my internet connection. What's gone wrong here?

---

### Post by Rex Bouwense on 2011-06-20
Open a terminal and type:
sudo apt-get update
You will have to enter your password.  After it is finished checking the repositories, you can type:
sudo apt-get upgrade

---

### Post by hopefulkayaker on 2011-06-20
Thank you! That worked.

---

### Post by westie457 on 2011-06-20
> **hopefulkayaker said:**
> On my desktop, I see a red triangle with an exclamation mark in it, next to the date at the top of my screen. Double-clicking on it brings up the update manager, which displays the following message:

"**Software updates may be available for your computer. **The package information was last updated 11 days ago. Press the 'Check' button below to check for new software updates."

After pressing the 'Check' button, a window appears with the title "Updating Cache". The another window appears in its place, saying:

"**Failed to download repository information **Check your internet connection." 

There's a details field which says:

```
W:Failed to fetch http://skulltag.net/download/files/release/deb/dists/stable/multiverse/source/Sources  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I have had no trouble with my internet connection. What's gone wrong here?

Hi, it could be the server where you download your updates from is having problems. My first suggestion is to change the server.

Open 'Synaptic' > Settings > repositories.
In the 'Ubuntu Software@ tab look for Download From and the the box choose a server close to your location. Click on 'Close'. Click on 'Reload' to refresh the changes you have done.
Then 'Edit' > 'Mark all Upgrades'. If there are any install them.

This should work for you. If not come back here to try something different

---

