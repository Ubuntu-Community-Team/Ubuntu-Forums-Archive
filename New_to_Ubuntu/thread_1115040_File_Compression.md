---
title: "File Compression"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by hedge2211 on 2009-04-03
I have been creating images of my hard drive to back it up but the images are very big, so i though that i should compress them so i was wondering what was the best compression tool to use.

Thanks

---

### Post by hovzio on 2009-04-03
gzip and bzip2 are good. I think gzip works together with tar for archiving. zip is also an option.

---

### Post by Hospadar on 2009-04-03
tarred gzips or bzips are probably your best bet, zip, while very standard and great for everyday things, doesn't compress as well as others.  Really, you could use whatever you want, it might be a good idea to experiment with a few (7zip, rar, etc) and see which ones give you the best compression.

Also, do you really need to back up with images of your disk?  Probably just saving of your home folder and maybe /etc would probably be good enough to get you going again and preserve important data.

---

### Post by billgoldberg on 2009-04-03
> **Hospadar said:**
> tarred gzips or bzips are probably your best bet, zip, while very standard and great for everyday things, doesn't compress as well as others.  Really, you could use whatever you want, it might be a good idea to experiment with a few (7zip, rar, etc) and see which ones give you the best compression.

Also, do you really need to back up with images of your disk?  Probably just saving of your home folder and maybe /etc would probably be good enough to get you going again and preserve important data.

7z should be superior.

---

### Post by binbash on 2009-04-03
I would prefer rar over 7z

---

### Post by mkvnmtr on 2009-04-03
If you go to the package manager and in the search box type file compression you will get a list of everything that you might use. Then you can read the descriptions of the programs that you might use and see which you think will work best for you. If you then don't like your pick you can try another. There are quite a few.

---

### Post by Yashiro on 2009-04-04
Just use tar.gz.

---

### Post by kaibob on 2009-04-04
The following page contains a chart with data on compression achieved by various file archivers (the smaller the % the better). I don't know how accurate this is, although it's been up for a while. The winner on compression appears to be 7-zip, although at the expense of longer compression times. 

[http://en.wikipedia.org/wiki/Comparison_of_file_archivers](http://en.wikipedia.org/wiki/Comparison_of_file_archivers)

I'm not a particularly patient person, so I would tend to go with one of the faster archivers, but that's just a matter of personal preference.

---

