---
title: "Creating a multipage PDF from scanned document"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by flyingsolo on 2009-05-10
I'm using Xsane to scan some documents to store digitally & I scan them in as PDFs.  However, each page is stored as a _separate_ PDF document; how can I combine several scanned pages to become one multi-page PDF?  In the end, I would like to open one document & scroll through the PDF pages with all related pages in one PDF document rather than open separate PDF's for each page.
Hopefully I've explained that clearly enough.  Sounds like it should be simple enough.
Thanks.

---

### Post by tajreed on 2009-05-10
Just did that. Select Multipage, then PDF for file type. It looks as if each PDF is an individual page but if you open the file it will read as a multi-page document.

---

### Post by unutbu on 2009-05-10
Install the pdftk package. Then to join input1.pdf and input2.pdf into output.pdf, in a terminal run:
```

pdftk input1.pdf input2.pdf cat output output.pdf
```

---

### Post by flyingsolo on 2009-05-10
Well see, I was right--it _was_ easy!  Though I feel like an eejit for not seeing that.
Thanks

---

### Post by flyingsolo on 2009-05-11
> **flyingsolo said:**
> Well see, I was right--it _was_ easy!  Though I feel like an eejit for not seeing that.
Thanks
So, maybe not so easy...I tried the 'multipage' xsane option and chose multipage document format as 'PDF' & it created a multipageproject file with 3 images of the 3 sheets I scanned but when I open one of the images, there is a blank file.  Also, the 3 images are .pnm files, not .pdf.  Am I missing something else simple?
Thanks again.

---

### Post by Pro-reason on 2009-05-25
> **flyingsolo said:**
> So, maybe not so easy...I tried the 'multipage' xsane option and chose multipage document format as 'PDF' & it created a multipageproject file with 3 images of the 3 sheets I scanned but when I open one of the images, there is a blank file.  Also, the 3 images are .pnm files, not .pdf.  Am I missing something else simple?
Thanks again.

I've found that if you set the project directory as ~/mystuff/mybooklet, then PNMs will be dumped into that directory, but the PDF will be in ~/mystuff.

---

