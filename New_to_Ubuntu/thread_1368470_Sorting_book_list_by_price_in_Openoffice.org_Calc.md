---
title: "Sorting book list by price in Openoffice.org Calc"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by hanzj on 2009-12-30
In my spreadsheet, Column A has the **titles** of the book, and Column B has the corresponding **price**.


For example.
```

**Title                            Price**
Cat in the Hat                     $5
Lord of the Rings                 $45
Fool Moon Rising                  $19
Calc for DumDums                 $230
```When I do Data/Sort/Sort By [Column B] Ascending, the prices do get sorted from smallest to biggest. That is good. But the titles in column A do not move with the price.

Please advise.

---

### Post by benfindlay on 2009-12-30
I think you need to select column A and B together, then sort by column B.

That work?

---

### Post by hanzj on 2009-12-30
Yes, that works.

You're right. the 2ndary sorting had to be column A.
Wonder why that is necessary. 

Wonder whether there are any spreadsheets where one needed a "column B" sorted without having the "Column A" match.

---

### Post by benfindlay on 2009-12-30
> **hanzj said:**
> Yes, that works.

You're right. the 2ndary sorting had to be column A.
Wonder why that is necessary. 

Wonder whether there are any spreadsheets where one needed a "column B" sorted without having the "Column A" match.

You may even be able to simply sort without a secondary column (i.e. just using B as a primary column) but with both columns still selected, as you may have many more than 2 columns, but only 1 important parameter to sort by.

The only time I can think you would need to sort 1 column on its own would be if it was a single dataset, that wasn't tied to another variable in any way.

---

### Post by Sir Jasper on 2009-12-30
Hi,

It is not a question of sorting column A, but of including column A in the range that gets sorted.

If you inserted a new column B (say Authors) so that the price is then listed in column C, and you had 100 titles. You could sort by any column (or columns), but you would have to specify the whole range of 3 columns and 100 rows if you want accurate results for all 100 titles.

My regards

---

### Post by hanzj on 2009-12-30
Oh, Sir Jasper, you're right. If the stuff in Column A is also selected/highlighted, then there's no need to do a secondary sort.

---

