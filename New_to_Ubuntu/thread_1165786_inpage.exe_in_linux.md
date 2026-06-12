---
title: "inpage.exe in linux??"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by faraz_k86 on 2009-05-21
most of you will be aware that inpage.exe is used to make urdu documents in windows... k so ive completely shifted to kubuntu now and need that program.. 

I have installed wine on my system but when i click on inpage.exe the wine icon starts jumping with the cursor showing its busy but after that nothing... nothing opens up.

has anyone been able to get urdu in linux?? and how can i get this to work?

thx

---

### Post by apjone on 2009-05-21
> **faraz_k86 said:**
> most of you will be aware that inpage.exe is used to make urdu documents in windows... k so ive completely shifted to kubuntu now and need that program.. 

I have installed wine on my system but when i click on inpage.exe the wine icon starts jumping with the cursor showing its busy but after that nothing... nothing opens up.

has anyone been able to get urdu in linux?? and how can i get this to work?

thx

Hey have you tried running this from a terminal? It maybe you need a certain dll adding to system32 area in wine.

Tony

---

### Post by faraz_k86 on 2009-05-22
so although inpage is a wine app will it work if i type "inpage.exe" in the terminal?

---

### Post by goldblattster on 2009-05-22
> **faraz_k86 said:**
> so although inpage is a wine app will it work if i type "inpage.exe" in the terminal?

No, it will not, as it is not an installed linux application. The computer needs to know the path of the executable. Plus, it is not a terminal. It's a Konsole! :p

Anyway, I do not know the main answer to your question, so here's a jolly bump to your thread!

---

### Post by Mark Phelps on 2009-05-22
If you're going to run apps in Wine, you need to familiarize yourself with the CodeWeavers compatibility database -- at the following link:

[http://www.codeweavers.com/compatibility/browse/name/?letter=i;]("http://www.codeweavers.com/compatibility/browse/name/?letter=i;")

You will see that inpage is not listed, meaning, it's not been tested by CodeWeavers with Wine.

---

### Post by Daveski on 2009-05-22
> **faraz_k86 said:**
> so although inpage is a wine app will it work if i type "inpage.exe" in the terminal?

Type ```
wine inpage.exe
```

---

### Post by durand on 2009-05-22
You could try to use the stuff that ubuntu has. I've had to type urdu once and I just installed the language stuff via the language configuration at System > Preferences, I think. I'm not on ubuntu at the moment so I don't know where exactly it is. I'm not really sure what inpage does but that might help.

---

### Post by horrerbaba on 2011-03-01
if Ubuntu not like or not run Inpage please share with us an alternative software then counting our work.

---

### Post by durand on 2011-03-01
Here you go, this should help: [http://maketecheasier.com/enable-foreign-language-input-in-ubuntu/2010/09/07](http://maketecheasier.com/enable-foreign-language-input-in-ubuntu/2010/09/07)

---

### Post by horrerbaba on 2011-03-07
thank for providing valuable info

> **durand said:**
> Here you go, this should help: [http://maketecheasier.com/enable-foreign-language-input-in-ubuntu/2010/09/07](http://maketecheasier.com/enable-foreign-language-input-in-ubuntu/2010/09/07)


but i have 1 more problem 

i want font "noori nastaliq".

---

### Post by durand on 2011-03-07
I'm not sure how you could use that one. There are a lot of others that are equally good though.

---

### Post by pjasnos on 2011-03-07
> **horrerbaba said:**
> thank for providing valuable info




but i have 1 more problem 

i want font "noori nastaliq".

This font isn't free - you can buy it from monotype: 
[http://www.monotypeimaging.com/ProductsServices/wt_fontsample.aspx?type=Arabic](http://www.monotypeimaging.com/ProductsServices/wt_fontsample.aspx?type=Arabic)

---

### Post by horrerbaba on 2011-03-08
dear sir,

my client required it because those are a law adviser and type all application and notice etc in Urdu and use "Noori Nastaliq".

i think understand my problem.


> **durand said:**
> I'm not sure how you could use that one. There are a lot of others that are equally good though.

---

### Post by Ghufran on 2012-04-08
I know this is too late but I want to help those who use Inpage and migrated to Linux.

There is no alternative or wine compatibility. The easy way to type Urdu in Ubuntu to setup your language settings by system setting > language support and then keyboard by system setting > keyboard layout

There is another way too to get this download and install this [debian package.]("http://makki.urducoder.com/wp-content/plugins/download-monitor/download.php?id=%D9%84%DB%8C%D9%86%DA%A9%D8%B3+%D8%A7%D8%B1%D8%AF%D9%88+%D8%A7%D9%86%D8%B3%D9%B9%D8%A7%D9%84%D8%B1+%28%DA%88%D9%90%D8%A8+%D9%BE%DB%8C%DA%A9%D8%AC%29")
[]("http://makki.urducoder.com/wp-content/plugins/download-monitor/download.php?id=%D9%84%DB%8C%D9%86%DA%A9%D8%B3+%D8%A7%D8%B1%D8%AF%D9%88+%D8%A7%D9%86%D8%B3%D9%B9%D8%A7%D9%84%D8%B1+%28%DA%88%D9%90%D8%A8+%D9%BE%DB%8C%DA%A9%D8%AC%29") [http://makki.urducoder.com/?page_id=1289&did=47](http://makki.urducoder.com/?page_id=1289&did=47)
This package has all necessary fonts for you. Including Jameel Noori Nastaleeq. 
To make your letters or any documentation use libre writer.
to get further help visit this urdu linux forum
[http://www.urducoder.com]("http://www.urducoder.com/")

---

