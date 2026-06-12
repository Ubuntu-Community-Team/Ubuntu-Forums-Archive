---
title: "trouble with foremost installation"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by Bootycelli on 2009-09-07
Hi folks, 
I used a simple copy/paste of the command lines given in the readme file of foremost and it simply doesn't work. Where did I go wrong ? Thanks for your advice.

 Here's the terminal reply:

$ tar zxvf foremost-xx.tar.gz 
tar: foremost-xx.tar.gz : la fonction open a échoué: Aucun fichier ou  dossier de ce type  (translation: function open failed: no file or  folder of that kind) 
tar: Erreur non récupérable : arrêt du traitement   (trans: error not  recoverable: program stop) 
tar: Child returned status 2 
tar: Des erreurs ont provoqué l'arrêt du programme   (errors provoked  program stop) 

PS you may have noticed I was french speaking...no one's perfect...

---

### Post by wojox on 2009-09-07
Try:

```
tar zxf foremost-xx.tar.gz 
```

---

### Post by Bootycelli on 2009-09-07
I just tried, same answer

---

### Post by Cheezespread on 2009-09-07
I am just wondering about the first error : "no file or  folder of that kind"

Questions :
1.Have you downloaded the zipped file?
2.Are you in the same directory where you saved the file ( in terminal)?

And I believe foremost is there in the Universal repos as well. You could try :
```
sudo aptitude install foremost
```

---

### Post by Bootycelli on 2009-09-07
wow,, 

Lecture des listes de paquets... Fait             
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait
Écriture de l'information d'état étendu... Fait

Does that talk to you ? The last line translates more or less as "writing of the extended state information...done"

What next ? 
Oh, by the way, thanks a lot for what looks like a good start...

---

### Post by Cheezespread on 2009-09-07
Sorry , I dont speak French. Are you gettig any errors like " Couldn't find any package " or something ?

Else I believe the installtion is done .After running the same , are you back in the terminal prompt ? 
You should probably have an entry in the Applications sections among one of the categories. ( Not sure which ). But some of the applications installed may not have it too. Can you type "foremost" in the terminal and see if it works ?

Just confirming : Foremost is the data recovery tool you want , right ? ( Apologies to have not asked this before).

---

### Post by Bootycelli on 2009-09-07
Yes, recovery is the goal
lost some important pictures while partitioning/installing ubuntu and crashing windows

I try to run foremost on the terminal

---

### Post by Bootycelli on 2009-09-07
Here's the answer

$ foremost
Processing: stdin
|



???

---

### Post by Cheezespread on 2009-09-07
> **Bootycelli said:**
> Here's the answer

$ foremost
Processing: stdin
|



???


Having not used it , I am unsure of the commands as well. Hope someone else could help you with the same. Found [this]("http://swik.net/foremost") link which directs how to use it. You can have a look into it.

If this doesn't help you , its better to ask it here ( Rather than doing something wrong) . Some one who has used it will surely help you out.

---

### Post by Bootycelli on 2009-09-07
Some news until now...
after using the link given by Cheezespread in his last post, here is what I got:

WMV err num_header_objs=-1610599280 headerSize=1283866582801590751

And now, what does that mean ? And how should I transform this into readable file ?

Thanks

---

