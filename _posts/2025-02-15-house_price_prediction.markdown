---
layout: post
title:  "House Price Prediction"
date:   2025-02-15 20:08:15 +0700
categories: projects
permalink: /projects/house_price_prediction
---

<script type="text/javascript" async
  src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" async
  id="MathJax-script" src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>


# **Tập dữ liệu**
Dữ liệu được cào từ trang batdongsan.com, gồm các thông tin cơ bản về **một căn nhà** như diện tíchm địa chỉ, số phòng, số tầng, v.v ở thành phồ Hồ Chí Minh. Tập dữ liệu chứa hơn 10 nghin dữ liệu, từ năm 2023 trở về trước.

# **Làm sạch dữ liệu**
Một bài đăng trên trang trông như sau:

<div style="display: flex; align-items: center;">
    <img src="/assets/images/house_price_prediction/estate_post.jpg" alt="Ảnh ví dụ" style="width: 50%; margin-right: 40px; margin-left: 40px; margin-bottom: 40px">
    <p>
        Phần khoanh <b><span style="color: green;">xanh lá</span></b> là tiêu đề bài đăng, phần khoanh <b><span style="color: orange">cam</span></b> là thông tin của bất động sản (hoặc là căn nhà), phần khoanh <b><span style="color: blue">xanh lam</span></b> là nội dung bài đăng.
    </p>
</div>

Khi cào dữ liệu, ban đầu, tôi chỉ lấy phần thông tin bất động sản, thế nhưng tôi nhận ra rằng có nhiều thông tin bị sai và không đồng nhất so với tiêu đề và nội dung. Vì vậy, tôi quyết định sử dụng `nltk` để tách thông tin thêm từ nội dung và tiêu đề và đối chứng. 

Ngoài ra, giá tiền có lẽ là phần khó xử lý nhất vì nó được nhập sai: đơn vị mặc định là _tỷ VND_, nếu giá bán là 3.9 _tỷ VND_ thì nhập 3.9 thay vì 3,900,000. Để làm sạch lại, ngoài phương pháp đối chứng nêu ở trên, tôi chia số đó cho $$10^3, 10^6, 10^9, 10^{12}$$ tùy trường hợp.