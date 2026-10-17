WEBSITE KY YEU LOP 12A6 - GITHUB PAGES + FIREBASE
=================================================

Tinh nang
---------
- Responsive mobile/desktop, danh sach 1 GVCN + 8 giao vien bo mon + 45 hoc sinh mau.
- Tim kiem/loc thanh vien, album ky niem, lightbox, thich anh, nhac nen, dark/light mode.
- Firebase Authentication (email/password) cho Admin.
- Cloud Firestore dong bo danh sach thanh vien va ky niem giua cac thiet bi.
- Admin them/sua/xoa thanh vien va them/sua/xoa ky niem.
- Sao luu/khoi phuc JSON. LocalStorage duoc giu lam cache du phong.

QUAN TRONG
----------
1. Khong dung lai tai khoan admin/yearbook123 cua ban demo cu.
2. Firebase web config co the hien trong ma nguon frontend; day khong phai mat khau.
   Bao mat that nam o Authentication va Firestore Security Rules.
3. Chi tai khoan co UID duoc phep trong rules moi duoc ghi/sua/xoa du lieu.
4. Du lieu thanh vien va ky niem doc duoc cong khai cho khach xem website.
5. Anh upload truc tiep gioi han 700 KB de tranh vuot gioi han kich thuoc document Firestore.
   Nen dung URL anh cong khai. Anh upload bang data URL se duoc luu trong document Firestore.
6. Chuc nang thich anh hien tai luu theo trinh duyet; luot thich chua dong bo toan cau.

CAU HINH FIREBASE TUNG BUOC
---------------------------
Buoc 1 - Tao Firebase project
1. Mo https://console.firebase.google.com/ va dang nhap Google.
2. Nhan Add project / Tao du an, dat ten vi du: 12a6-yearbook.
3. Trong Project Overview, nhan icon Web (</>) de them web app.
4. Dat nickname: 12A6 Yearbook. Dang ky app va giu lai firebaseConfig hien ra.

Buoc 2 - Bat dang nhap Admin
1. Firebase Console > Build > Authentication > Get started.
2. Tab Sign-in method > Email/Password > Enable > Save.
3. Tab Users > Add user, tao email va mat khau rieng cho Admin.
4. Sao chep UID cua user vua tao. Khong tao chuc nang dang ky cong khai tren website.

Buoc 3 - Tao Firestore
1. Build > Firestore Database > Create database.
2. Chon production mode neu duoc hoi va chon region gan nguoi dung (vi du asia-southeast1 neu co).
3. Sau khi tao xong, mo tab Rules.
4. Mo file firestore.rules kem theo goi nay.
5. Thay ca hai chuoi YOUR_ADMIN_UID bang UID Admin vua sao chep.
6. Dan rules vao tab Rules trong Firebase Console va nhan Publish.
   Rules cho phep moi nguoi DOC danh sach lop, nhung chi UID Admin duoc them/sua/xoa.
   KHONG dung test mode / allow read, write: if true cho website cong khai.

Buoc 4 - Gan Firebase vao index.html
1. Mo index.html bang VS Code, Notepad++ hoac editor van ban.
2. Tim khoi:
   const firebaseConfig={apiKey:'PASTE_API_KEY',authDomain:'PASTE_PROJECT_ID.firebaseapp.com',projectId:'PASTE_PROJECT_ID',appId:'PASTE_APP_ID'};
   const ADMIN_UID='PASTE_ADMIN_UID';
3. Thay cac gia tri firebaseConfig bang gia tri chinh xac trong Firebase Console:
   Project settings (bieu tuong banh rang) > General > Your apps > SDK setup and configuration.
   Can cac truong apiKey, authDomain, projectId, appId.
4. Thay PASTE_ADMIN_UID bang UID Admin o Buoc 2 (giu dau nhay don).
5. Khong dua mat khau Admin vao index.html, README hoac repository.

Buoc 5 - Cho phep domain dang nhap
1. Authentication > Settings > Authorized domains.
2. Dam bao co domain dang dung, them 12A6.sweep.id.vn neu chua co.
3. Neu ban thu nghiem bang ten github.io, them host github.io neu Firebase yeu cau.

Buoc 6 - Day len GitHub Pages
1. Tao repository GitHub, vi du 12A6-yearbook.
2. Upload cac file trong thu muc nay vao ROOT repository:
   index.html, README.txt, firestore.rules
   (index.html phai nam o root, khong nam trong thu muc con.)
3. Repository > Settings > Pages > Deploy from a branch > main > /(root) > Save.
4. Trong Custom domain nhap 12A6.sweep.id.vn va Save.
5. Trong Cloudflare DNS tao CNAME:
   Type: CNAME | Name: 12A6 | Target: TEN-GITHUB.github.io | Proxy: DNS only
   Thay TEN-GITHUB bang username GitHub that cua ban.
6. Cho DNS cap nhat, sau do bat Enforce HTTPS trong GitHub Pages.
7. Mo https://12A6.sweep.id.vn va kiem tra website.

Buoc 7 - Nap du lieu mau len cloud lan dau
1. Mo website, bam Quan tri.
2. Dang nhap bang email/mat khau da tao trong Firebase Authentication.
3. Bam nut "Day du lieu mau len Cloud".
4. Xac nhan de nap 1 GVCN, 8 giao vien, 45 hoc sinh va 6 ky niem mau vao Firestore.
   Neu Firestore da co du lieu, thao tac nay cap nhat document trung ID va xoa document
   cloud khong co trong danh sach dang hien thi. Hay sao luu truoc neu da co du lieu that.
5. Mo website tren dien thoai/may tinh khac; danh sach va ky niem se tai tu Firestore.

SU DUNG ADMIN
-------------
- Bam Quan tri > dang nhap email/mat khau Firebase.
- Them/sua/xoa thanh vien trong phan danh sach thanh vien.
- Them/sua/xoa ky niem trong phan Quan ly ky niem.
- De dong bo anh dung URL anh cong khai, hoac upload anh nho hon 700 KB.
- Neu thay loi permission-denied, kiem tra UID trong index.html va firestore.rules phai giong nhau,
  sau do Publish lai rules.
- Neu website khong tai du lieu, kiem tra firebaseConfig, Firestore da tao, va tab Console cua trinh duyet.

GHI CHU
-------
- Firebase API key web khong phai bi mat; tuy nhien rules phai khoa ghi du lieu theo UID Admin.
- Khong tao them tai khoan Admin cho nguoi khong tin cay.
- Firestore co han muc mien phi va tinh phi neu vuot han muc; theo doi Usage trong Firebase Console.
- Luot thich anh hien tai la tren tung trinh duyet, chua duoc dong bo toan cau.
- File index.html su dung Firebase compat SDK tu CDN, khong can npm build.
