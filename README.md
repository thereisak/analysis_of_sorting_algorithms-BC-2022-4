
【问题描述】
内部排序算法在数据结构课程及实际应用中都具有重要的地位。同时不同的算法具有不同的时间复杂度。试通过随机数据比较各种单关键字排序算法的关键字比较次数和关键字移动次数。并能适当可视化演示。

【任务要求】

1)	实现以下7种常用的内部排序算法，并进行比较：冒泡排序、直接插入排序、简单选择排序、希尔排序、堆排序、归并排序、快速排序。

2)	待排序表的表长不小于100；其中的数据要用伪随机数程序产生；随机产生多组数据进行比较分析，给出平均情况性能和最坏情况性能。比较的指标为有关键字参加的比较次数和关键字的移动次数（关键字交换计为3次移动）。

3)	可视化显示各排序算法的效果。

【测试数据】

随机产生，可设定在某个范围内的随机数。

【算法思想】

以下算法均选择升序排序

1.冒泡排序

冒泡排序相当于做n-1趟冒泡，每趟冒泡比较所有相邻的元素，如果前一个比后一个大，就交换它们两个，这样在最后的元素会是最大的数，下一趟冒泡不再比较最后一个元素（即L->Length-i+1），这样n-1趟冒泡后数据就会从小到大排列。同时若一趟冒泡没有产生交换，则表已经有序，跳出大循环。

2.直接插入排序

直接插入排序将表分为前后两段表，前段为有序表，后段为无序表，从第一个元素开始，该元素可以认为已经有序；取出无序表下一个元素，存到哨兵位置，在已经排序的元素序列中从后向前比较；如果已排序元素大于新元素，将该元素向后移动一个位置，再比较，直到找到已排序的元素小于或者等于哨兵元素的位置，将哨兵元素插入到腾出的位置；进行n-1趟插入操作后原表变为有序表。

3.简单选择排序

首先在未排序表中找到最小元素，（即选初始位置为哨兵，与后面的元素比较，保留最小的位置），与起始位置的值交换；然后，再从剩余未排序元素中继续寻找最小元素，然后放到已排序序列的末尾；重复n-1趟，原表变为有序表。

4.希尔排序

希尔排序的思想是先将整个待排序的表列分割成为若干个子表，分别进行直接插入排序。 

首先选择一个增量序列d1，d2，…，dk，其中di>tj，i<j,dk=1；按增量序列个数k，对序列进行k 趟排序；每趟排序，根据对应的增量di（di>1），将待排序列分割成di-1个子表，每个子表元素为原表中间隔di个位置的元素集，再分别对各子表进行直接插入排序；当增量为1 时，相当于按整个表做一趟直接插入排序，原表变为有序表。


5.堆排序

堆排序的基本思想是将待排序序列构造成一个大顶堆，此时，整个表的最大值就是堆顶的根节点，将其与末尾元素进行交换，那么末尾就为最大值；然后将剩余n-1个元素重新构造成一个大顶堆，这样会得到n个元素的次小值。重复交换调整，最后得到一个有序表。具体步骤为：

a.将原始序列初始化为大顶堆，从最后一个非终端节点开始向上调整；

b.将堆顶元素与末尾元素交换，则最大元素排到末端；

c.从堆顶到叶子进行“筛选”，重新调整得到大顶堆；

d.重复b,c直到原始序列有序。

6.归并排序

归并排序的思想是将原始序列先分解成n个长度为1的子序列，然后两两归并，得到[n/2]个长度为2或1有序子序列，再两两归并……，直到得到一个长度为n的有序序列。具体步骤为：

a.分解: 将当原始序列一分为二，中间点为 mid = (start + end)/2；

b.求解：递归地对两个子序列L.r[start...mid]和L.r[mid+1...end]进行归并排序,终止条件是子序列长度为1，即到最后得到n个子序列；

c.合并：将表中已排序的两个子序列L.r[start...mid]和L.r[mid+1...end]归并为一个有序的序列L.r[start...end]。

递归结束后原始序列变为有序序列。

7.快速排序

快速排序的基本思想是通过一趟排序将表分隔成独立的两部分，其中前部分的关键字均比另一部分的关键字小，再分别对这两部分记录继续进行排序，直到整个表有序。具体步骤为：

a.先选一个枢轴（中间量），通常为第一个元素，保存到哨兵，定义两个指针low，high，其中low指向表头，high指向末尾；

b.指针high向前移动，找到比哨兵小的元素，赋值到枢轴的位置，该元素原来的位置作为枢轴，low向后移动，直到找到比哨兵大的元素，赋值到枢轴位置，同样该元素原来的位置作为枢轴；当low与high重合时，将哨兵的值赋值到重合的位置，即枢轴正确的位置。

c.对正确的枢轴位置前半部分和后半部分递归调用a,b操作，原表变为有序表，终止条件为low>=high。

【实验结果】
实验的结果主要分三部分，首先界面如下图
 ![image](https://user-images.githubusercontent.com/69351898/162557887-9976a44c-dbca-4f85-af49-1a899a4fae8f.png)

1. 随机产生一组伪随机数，显示各个算法排序结果

伪随机数采用的是以时间为种子的随机数，srand( (unsigned int)time(NULL)+gap++);

数据范围是1~100，待排序表的表长定为100，产生一组伪随机数后，调用各个算法显示排序结果，如下图，可以看到都能正常给出升序排序结果，

![image](https://user-images.githubusercontent.com/69351898/162557890-873f5696-7d10-4ff9-acc2-8c8f46b4616f.png)

2.选择一个算法，可视化算法步骤

操作2的界面如图，
 
 ![image](https://user-images.githubusercontent.com/69351898/162557896-d80114b3-f89d-46bb-9589-7fa645531a36.png)

选择相应的排序算法能可视化算法的排序步骤和效果，部分效果如下图，

 ![image](https://user-images.githubusercontent.com/69351898/162557900-6fd3fe18-c47f-479f-a675-bfec5c51c5ab.png)
![image](https://user-images.githubusercontent.com/69351898/162557904-f200d56f-ff28-4506-a5bd-37d48f886b42.png)
![image](https://user-images.githubusercontent.com/69351898/162557906-80e1d7f0-d3fd-4dd3-a36d-fd4fc64523a0.png)

 
 
 
3.随机产生多组数据比较分析，显示平均情况性能和最坏情况性能

产生的组数为10~20组之间，比较的指标为有关键字参加的比较次数和关键字的移动次数（关键字交换计为3次移动）。结果如下图，
伪随机数如下

 ![image](https://user-images.githubusercontent.com/69351898/162557911-b12ae508-32a2-4308-b24b-418e57580f5b.png)

比较结果如下

![image](https://user-images.githubusercontent.com/69351898/162557918-b1681e7b-2bfd-4bbc-9b58-4afe6d8ac06a.png)

 续表
 
 ![image](https://user-images.githubusercontent.com/69351898/162557919-db2436df-94f6-4576-8cfd-d93ba4d53332.png)


从结果中发现，快速排序平均情况性能最好，归并排序次之，接下来依次是希尔排序、堆排序、直接插入排序、简单选择排序、冒泡排序。原因可能是数据量比较少，快速排序、希尔排序效果比较好，而堆排序效果不显著。

【实验总结】

各个算法的平均情况和最坏情况性能如下

排序方法	时间复杂度(平均情况) 	时间复杂度(最坏情况）

冒泡排序	    O(n^2)	               O(n^2)

直接插入排序	O(n^2)        	       O(n^2)

简单选择排序	O(n^2)        	      O(n^2)

希尔排序	    O(nlog2n)~O(n^2)	    O(n^2)

堆排序	       O(nlog2n)	           O(nlog2n)

归并排序	    O(nlog2n)	            O(nlog2n)

快速排序  	  O(nlog2n)	            O(n^2)

 可以发现堆排序、归并排序、快速排序、希尔排序的平均情况性能比较好，冒泡排序、直接插入排序、简单选择排序平均情况性能较差，与实验结果基本吻合。
