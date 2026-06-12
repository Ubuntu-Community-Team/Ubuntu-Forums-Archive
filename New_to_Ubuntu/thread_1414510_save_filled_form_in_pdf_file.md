---
title: "save filled form in pdf file"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by flylehe on 2010-02-23
Hi,

I would like to save a pdf file with filled out interactive form. In evince or acrobat reader, "Print to file" can create another pdf file but the form is not editable any more. Is there some way to save the edit and keep the form interactive for later editing?

Thanks and regards!

---

### Post by tadcan on 2010-02-23
The only way I know is to have adobe professional.

---

### Post by spcwingo on 2010-02-23
You can always edit it later with pdfedit.  You can install it with this command:

```
sudo apt-get install pdfedit
```

---

### Post by flylehe on 2010-02-23
Does it have Ubuntu version?

> **tadcan said:**
> The only way I know is to have adobe professional.

---

### Post by flylehe on 2010-02-23
I just tried it. For a pdf file with interactive form created in Adobe Professional, how can I make input into the form? It seems pdfedit does not recognize the form?

Here is the pdf file whose forms I am trying to fill out&#65306;[http://grad.jhu.edu/downloads/Applied%20Math%20Supplementary%20Application%20Form%202009-2010.pdf](http://grad.jhu.edu/downloads/Applied%20Math%20Supplementary%20Application%20Form%202009-2010.pdf)
When I click edit->select notations and try to click an entry of the forms, there will be an error
> 
TypeError. 'go_to_target_from_selected_annotation' undefined or not a function".

I wonder what are the correct steps to make and save input to the forms in pdfedit?

> **spcwingo said:**
> You can always edit it later with pdfedit.  You can install it with this command:

```
sudo apt-get install pdfedit
```

---

### Post by tadcan on 2010-02-23
> **flylehe said:**
> Does it have Ubuntu version?

Not that I'm aware of. TBH advanced pdf is hard to do under linux, so I don't.

---

### Post by donato roque on 2010-02-23
There's a good list of pdf editing tools in this article at[ Ubuntu Geek.]("http://www.ubuntugeek.com/list-of-pdf-editing-tools-for-ubuntu.html")
I don't use any of it though so I can't tell how good they work personally.

---

