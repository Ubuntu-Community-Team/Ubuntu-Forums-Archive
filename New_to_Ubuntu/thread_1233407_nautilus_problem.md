---
title: "nautilus problem"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Dontechjuan on 2009-08-06
hi im new to linux and i made an idiot mistake while trying to rid myself of an annoyance. after a while of using ubuntu something was beginning to use all my processing capacity for the first 30 minutes after turning my computer on. Using "system monitor" i found that nautilus was using it all because it was making and scanning thumbnails it had made of every image on my computer and every image looked at through the internet making 40,000+ copies with many of them doubles, triples ect. i deleted the thumbnails but every time i turn my computer on it would start the process of making thumbnails all over again. at first i didnt notice this but when it bogged my computer down again i found that it was still making more thumbnails. i got tired of deleting them all after every session in order to keep it from bogging it down again and decided to delete nautilus not knowing what its purpose was for. but it kept popping up again every time i opened the home folder, so to keep it from coming back i made a text document named .nautilus knowing that it wouldn't be able to remake the folder named .nautilus if there was already a doc file with the same name. it worked but now i know what nautilus was supposed to do. without it being able to make the correct folder all my desktop icons wont show up and i cannot access any folders without it. so the issue im faced with is trying to remove, rename or relocate the doc file i made so that nautilus can pop back up but i have to do this without being able to access any folders. i tried opening text editor using the drop down menu and trying to replace it or trash it, rename or something but the "open file" option in the text editor doesn't allow any options like that and so far the "open file" option on text editor is the only way I've found to even see whats in my home folder. I've also tried reinstalling it but the "synaptic package manager" only gives me the option to "remove" it and i didn't want to try that in fear it may make more of my computer inaccessible. please help me figure out how to get rid of this doc file i made so nautilus can come back.

---

### Post by pedro3005 on 2009-08-06
Applications > Accessories > Terminal. Type 'sudo rm /home/user/.nautilus'. Replace user with your user name. I don't know why nautilus would be doing what you described, it is very strange.

---

### Post by Clorow on 2009-08-06
Actually, once you open up the terminal, all you have to do is type:
```
rm .nautilus
```
You don't need sudo, and you don't even need your username. It's that simple.

---

### Post by pedro3005 on 2009-08-06
Yeah, my lack of attention's fault lol. Sorry :)

---

### Post by Dontechjuan on 2009-08-06
awesome that did it. thank you very much my friend. ya i though it was weird also but according to system monitor nautilus made a folder called .thumbnails and when i opened it that 1st time it had over 100,000 miniature images of every image i have ever accessed and after deleting them all and freeing up the processor, after every session i would check the thumbnails folder and there would be 40,000+ new .png files meaning it started doing it all over again. now that the nautilus folder is back i'll have to go back to deleting the thumbnails after every session again:( as a matter of fact i have had nautilus back for about 3 minutes and it already copied 103 mini images of images in my hardrive and i havent viewed any images since I brought nautilus back. if any of you know why it does this or how to get it to stop please let me know.

---

