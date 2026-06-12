---
title: "pdf to jpg/mpeg"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by dondecap on 2011-05-31
hello
I need to convert pdf to jpg to make a slide show to view on tv/dvd
I used gimp but the text was unreadable.
I have seen to use , Imagemagick
so found it and installed it but is there no 'user interface'?
not in menu so an trying 'iphotowizard' ...not very succesfully I may add.
help please
regards
don

---

### Post by Ken UK on 2011-05-31
Go back to Gimp as you can't get any better results from anything else. Remember to choose a resolution when importing a PDF which is detailed enough for what you need it. If the image is fuzzy its likely the resolution is too low.

---

### Post by howefield on 2011-05-31
Try opening a terminal and use the "convert" command.

Eg,

```
convert input_file_name output_file_name
```

---

### Post by jobjol on 2012-07-27
Don't forget to add -colorspace RGB to your command.
I use this command and it gives you a very high quality and clear JPG file:"

```
convert -density 300x300 [input-pdf-file] -colorspace RGB -quality 90 [output-jpg-file]
```

You can check the output quality of the command above @ [pdfjpg.net]("http://pdfjpg.net")

Regards,

JJ

---

### Post by Elfy on 2012-07-27
Old thread closed.

---

