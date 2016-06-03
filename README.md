# gaussian elimination

function z = gaussian(A,b)

n = length(b); z = zeros(n,1);
    
    for j = 1:n-1
        for i = j+1:n
         mult = A(i,j)/A(j,j);
         for k = j+1:n
            A(i,k) = A(i,k) - mult*A(j,k);
         end
         b(i) = b(i) - mult*b(j);
        end
    end
    
    z(n) = b(n)/A(n,n);
    for i = n-1:-1:1
        sum = b(i);
        for j = i+1:n
            sum = sum-A(i,j)*z(j);
        end
        z(i) = sum/A(i,i);
    end
end
