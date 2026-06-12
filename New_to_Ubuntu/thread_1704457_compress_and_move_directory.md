---
title: "compress and move directory"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-03-10
how do I compress a directory then move it to another hard drive in one command?

right now i have to tar -czvf /windows/files/compress 
then cp -v /windows/files/compress /other-hard-drive/windows/compress

is there a way to use the tar command to do all this?

---

### Post by GWBouge on 2011-03-10
Tell it the output file, and create the archive where you want it instead of copying it.

```

# tar -czvf [output_file] [input]
tar -czvf /other-hard-drive/windows/compress.tar /windows/files/compress
```

---

