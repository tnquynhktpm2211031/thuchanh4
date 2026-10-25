# Hướng dẫn thực hành Git — Buổi 4

Tài khoản GitHub: `tnquynhktpm2211031`  
Repository: https://github.com/tnquynhktpm2211031/thuchanh4.git  
Tên Git đề xuất: `nhuquynh`  
Email: `tnquynhktpm2211031@student.ctuet.edu.vn`

> Lưu ý: Những thao tác trong repository được thực hiện từ xa không phải là bằng chứng chạy lệnh trên Ubuntu. Hãy chạy và tự chụp ảnh Terminal cho các mục yêu cầu minh chứng.

## A. Cài đặt và Git cơ bản (1–9)
```bash
git --version
git config --global user.name "nhuquynh"
git config --global user.email "tnquynhktpm2211031@student.ctuet.edu.vn"
git config --global --list
git clone https://github.com/tnquynhktpm2211031/thuchanh4.git
cd thuchanh4
git status
git log --oneline
echo "Them dong thuc hanh" >> practice.txt
git diff
git add practice.txt
git status
git commit -m "Practice Git staging"
git log --oneline
echo "*.log" >> .gitignore
git add .gitignore
git commit -m "Update ignore rules"
# Chi amend commit CHUA push:
git commit --amend -m "Update gitignore rules"
```

## B. Nhánh và hợp nhất (10–17)
```bash
git switch -c feature/local-practice
echo "Tinh nang moi" >> practice.txt
git add practice.txt
git commit -m "Implement local feature"
git switch main
git merge feature/local-practice
git branch -d feature/local-practice
git log --oneline --graph --all
git branch demo-old
git branch -m demo-old demo-renamed
git branch -D demo-renamed
```
Câu 16: tạo hai nhánh sửa cùng một dòng trong một tệp, thực hiện merge, sửa dấu conflict, `git add` và `git commit`; nên thực hành trên nhánh thử nghiệm.  
Câu 17: tạo nhánh riêng rồi dùng `git rebase main`; lịch sử rebase khác với merge vì thay đổi commit nền và hash.

## C. GitHub (18–27)
```bash
git remote -v
git remote set-url origin https://github.com/tnquynhktpm2211031/thuchanh4.git
git push -u origin main
git clone https://github.com/tnquynhktpm2211031/thuchanh4.git thuchanh4-copy
git branch -r
git pull origin main
git switch -c feature/pull-request-local
echo "Noi dung PR" >> practice.txt
git add practice.txt
git commit -m "Add PR content"
git push -u origin feature/pull-request-local
git tag v1.0.0
git push origin v1.0.0
ssh-keygen -t ed25519 -C "tnquynhktpm2211031@student.ctuet.edu.vn"
cat ~/.ssh/id_ed25519.pub
# Them public key vao GitHub > Settings > SSH and GPG keys
ssh -T git@github.com
```
Câu 23: mở Pull Request trên giao diện GitHub từ nhánh feature vào main.  
Câu 24: muốn tạo Release phải mở trang Releases và chọn Create a new release.  
Câu 25: xuất bản GitHub Pages cần cấu hình Settings > Pages, nếu được phép.  
Câu 27: chỉ thêm remote thứ hai sau khi có URL giảng viên cung cấp: `git remote add backup URL`.

## D. Kiểm tra, khôi phục, tìm lỗi (28–36)
```bash
echo "Ban nhap" >> practice.txt
git restore practice.txt
echo "Ban nhap" >> practice.txt
git add practice.txt
git restore --staged practice.txt
git restore practice.txt
git log --oneline -- practice.txt
git show HEAD:practice.txt
git restore --source=HEAD~1 -- practice.txt
git grep "Git"
git reflog
git bisect start
# Can commit good/bad thuc te de tiep tuc bisect
git bisect reset
# Hoan tac commit da push an toan: git revert <commit-hash>
```
Câu 30: `git rm --cached <ten-tep-da-theo-doi>` chỉ ngừng theo dõi trong Git và giữ bản local.  
Câu 31: `git show <hash>:practice.txt` đọc nội dung tệp tại commit chọn.  
Câu 34–36 phải dùng commit có thật; không tự bịa mã hash.

## E. Nâng cao (37–41)
```bash
echo "Dang lam do" >> practice.txt
git stash push -m "tam cat thay doi"
git stash list
git stash pop
git config --global alias.st "status"
git config --global alias.lg "log --oneline --graph --all"
git st
git lg
# Câu 39: git submodule add <URL-repository-duoc-phep> thu-muc-con
git status
git log --oneline --graph --all
```

## Trạng thái minh chứng
Những tệp/commit/nhánh thực tế có trên GitHub có thể kiểm chứng trực tiếp. Không xem câu 1–17 hay 26–40 đã được hoàn thành trên máy Ubuntu chỉ vì có hướng dẫn lệnh trên đây. Khi nộp bài, hãy chụp màn hình Ubuntu thực tế và đánh dấu các bước đã tự chạy.
