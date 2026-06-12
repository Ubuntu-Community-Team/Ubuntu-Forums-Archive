---
title: "replace values in column"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by daveli on 2011-02-11
Hi,

I have a large tab-del file like this

Mt      protein_coding  exon    273     734     .       -       .        gene_id "ATMG00010"; transcript_id "ATMG00010.1"; exon_number "1"; gene_name "ORF153A"; transcript_name "ATMG00010.1";
Mt      protein_coding  CDS     276     734     .       -       0        gene_id "ATMG00010"; transcript_id "ATMG00010.1"; exon_number "1"; gene_name "ORF153A"; transcript_name "ATMG00010.1";
Mt      protein_coding  start_codon     732     734     .       -       0        gene_id "ATMG00010"; transcript_id "ATMG00010.1"; exon_number "1"; gene_name "ORF153A"; transcript_name "ATMG00010.1";
.
.
.

The first column has different values (Mt, 1, 2, ...) and I want to add chr to each of them, so I get chrMt when Mt was present, chr1 when 1 is present, etc... How can I do that?

Thanks for your help

D.

---

### Post by The Cog on 2011-02-11
How about something like this:
```
sed 's/^/chr/' inputFileName > outputFileName
```

---

### Post by daveli on 2011-02-14
Great! thanks a lot The Cog!

---

