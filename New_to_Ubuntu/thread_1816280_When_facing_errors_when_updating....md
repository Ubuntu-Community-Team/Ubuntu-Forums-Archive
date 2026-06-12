---
title: "When facing errors when updating..."
date: 2011-08-01
forum: New to Ubuntu
---

### Post by sffvba[e0rt on 2011-08-01
I have been getting the following error (and similar ones) for many weeks:

> W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages  Hash Sum mismatch , E:Some index files failed to download. They have been ignored, or old ones used instead.I found that normally they would resolve themselves, but in this case it didn't.  Now having solved this issue by running the the commands below I was shocked to find I had 133mb of updates that I have been missing out on for some time now... some of them might be important and I am annoyed I hadn't rectified this error sooner.

So if you face similar and everything you normally try (like changing server) has failed, try this:

                                 > sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update


Regards
404

---

