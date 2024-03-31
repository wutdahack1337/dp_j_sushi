# dp_j_sushi
dp_j thiệt là nhức cái đầu

Hôm nay làm bài [Sushi](https://atcoder.jp/contests/dp/tasks/dp_j), nó kêu tính giá trị kỳ vọng, sau khi suy nghĩ nửa ngày không ra, đọc sol nửa ngày cũng không hiểu. Nhưng may mắn thay, t kiếm thấy một cái sol dễ hiểu, t để đây để t của tương lai coi lại.

Gọi **f[a][b][c]** là số lượt kỳ vọng để ăn hết 1a + 2b + 3c cái sushi trên n dĩa. Cho **k** = a + b + c

f[a][b][c] = (f[a][b][c] + 1) * $\frac{n-k}{n}$ + (f[a-1][b][c] + 1) * $\frac{a}{n}$ + (f[a+1][b-1][c] + 1) * $\frac{b}{n}$ + (f[a][b+1][c-1] + 1) * $\frac{c}{n}$  
= f[a][b][c] * $\frac{n-k}{n}$ + f[a-1][b][c] * $\frac{a}{n}$ + f[a+1][b-1][c] * $\frac{b}{n}$ + f[a][b+1][c-1] * $\frac{c}{n}$ + 1  
<=> f[a][b][c] - f[a][b][c] * $\frac{n-k}{n}$ = f[a][b][c] * $\frac{k}{n}$ = f[a-1][b][c] * $\frac{a}{n}$ + f[a+1][b-1][c] * $\frac{b}{n}$ + f[a][b+1][c-1] * $\frac{c}{n}$ + 1  
<=> f[a][b][c] = f[a-1][b][c] * $\frac{a}{k}$ + f[a+1][b-1][c] * $\frac{b}{k}$ + f[a][b+1][c-1] * $\frac{c}{k}$ + $\frac{n}{k}$  
<=> f[a][b][c] = $\frac{f[a-1][b][c] * a + f[a+1][b-1][c] * b + f[a][b+1][c-1] * c + n}{k}$  
<=> f[a][b][c] = $\frac{f[a-1][b][c] * a + f[a+1][b-1][c] * b + f[a][b+1][c-1] * c + n}{a+b+c}$  
