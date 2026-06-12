---
title: "I'm a bit frustrated by Synaptic Package Manager"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Net_Resident on 2009-04-04
The problem I have is with the filtering. I find myself often with too large a selection and not having a comprehensive drill down method. For example, if I wanted to search an exact phrase in a web search engine I could use quotation marks. Or if I want to search based on a few words it would find all entry's that contain all of the words I used, instead what it does is find all entry's with any of the words I used which expands the choices, not narrows them down.

I'm hoping that I'm just ignorant of a better way but so far I haven't found it. Using the repository filters doesn't do what I am requesting. Is there a better way to *drill down*? :)

---

### Post by ktrnka on 2009-04-04
You can set a filter under Settings>Filters and Select the Search Filter and click the Properties tab. You can add your settings there. I personally prefer to use apt-cache from the terminal (Applications>Terminal) because you can pipe the output to grep:

```
sudo apt-cache search FILEorPACKAGENAME | grep ADDITIONALparametersTOSearch
```

Example to find the mplayer plugin for firefox

```
sudo apt-cache search browser|grep mozilla|grep mplayer
```

and you can keep adding parameters you are looking for by continuing to add |grep PARAMETER

It returns ```
mozilla-mplayer - MPlayer-Plugin for Mozilla
```

I can then install it by:
```
sudo apt-get install mozilla-mplayer
```

and you can even pipe the output to the less command allowing you to scroll through the list.

I find this way much easier than any other way.

---

### Post by Net_Resident on 2009-04-04
I suppose Grep is useful but with the manager you have more encompassing features and options at a view than you do with CLI. At a glance I can see a range of offerings, what their installed status is, what the version is. I can then go down to the description area and get more information without losing where I was or entering more commands. Don't get me wrong, I'm not anti CLI, I'm just not that familiar with all CLI commands and it seems to me that there is more information at a glance with the GUI.

---

### Post by pbpersson on 2009-04-04
I am anti-command line  :)

Have you tried searching the online repository to see if you can use search strings there?

I think that might show you a bunch of information, but not what you have installed on your machine.

---

### Post by Net_Resident on 2009-04-05
> **pbpersson said:**
> Have you tried searching the online repository to see if you can use search strings there?
No, I hadn't thought of that. Where do I start? :)

---

