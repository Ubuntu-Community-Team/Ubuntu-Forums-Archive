---
title: "Print PDF over network"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by serhito on 2007-12-11
Hi,

It seems that I have found a way to use my non Linux printer to print from Ubuntu.
I have an old laptop that I use as a server. I installed on it an application that whenever a file goes into a specific folder, it will automatically print it.
My idea is to print in Ubuntu as PDF straight over the network into that folder.
There is a way to change the output directory in the cups-pdf.conf file, but I cannot find which network path to write. I tried a simple smb://computer/folder, but that doesn't work.

The other way would be to Map the folder that prints, but I don't know how to do that.
I haven't found a good tutorial.

Any idea ?

---

### Post by mpokrywka on 2007-12-11
You can "map" smb folder by using mount -t cifs.
You need smbfs package installed.

Simple use:
mount -t cifs //server/print_dir /dir/for/cups/to/store/pdf -o user=username,password=secret

For detailed use consult **man mount.cifs**.

---

