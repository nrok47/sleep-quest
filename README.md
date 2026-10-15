# Sleep Quest: ภารกิจพิชิตราชาผีอำ (HPC10 Lifestyle Medicine x Sleep Lab)

มินิเกมประเมินสุขอนามัยการนอนและคัดกรองภาวะหยุดหายใจขณะหลับ (OSA) บน **LINE LIFF**  
เน้นแนวคิด **"สร้างนำซ่อม"**: ให้ความรู้ Lifestyle Medicine (สร้าง) + คัดกรองส่งต่อคลินิกหลับดี ศอ.10 (ซ่อม)

---

## 🚀 ฟีเจอร์หลัก (LINE-Native)

1. **Auto-Profile:** ดึงรูปและชื่อจากบัญชี LINE ของผู้เล่นอัตโนมัติ (`liff.getProfile()`) ไม่ต้องพิมพ์ชื่อใหม่
2. **Card Battle 3 เทิร์น:**
   - Turn 1: Sleep Hygiene (เที่ยงคืนตาสว่าง)
   - Turn 2: OSA Screening (เสียงกรนสนั่นบ้าน)
   - Turn 3: EDS Screening (ตื่นนอนแล้วเพลีย/หลับใน)
3. **ระบบ "เอ๊ะ!" (Health Literacy):** สอดแทรกกลลวงความเชื่อผิดๆ เพื่อกระตุกต่อมเอ๊ะและให้ความรู้ที่ถูกต้อง
4. **Viral Loop (LINE Share Target Picker):** ปุ่มชวนเพื่อน/คนข้างตัวที่นอนกรนมาลองเล่นต่อใน LINE
5. **Call to Action (ศอ.10 Sleep Lab):** ปุ่มทักแชทคุยกับพี่ค้าง / กรอกเบอร์ขอคำปรึกษาฟรี

---

## 🛠️ ขั้นตอนเปิดใช้งานบน LINE LIFF (ฟรี 100%)

### 1. โฮสต์ไฟล์ `index.html` ขึ้น Web ฟรี
เลือกช่องทางใดช่องทางหนึ่ง:
- **GitHub Pages (แนะนำ):** สร้าง Repo ใหม่บน GitHub (เช่น `nrok47/sleep-quest`) แล้วเปิด Settings -> Pages -> Deploy from main branch จะได้ URL เช่น `https://nrok47.github.io/sleep-quest/`
- **Cloudflare Pages:** อัปโหลดโฟลเดอร์นี้ตรงๆ ได้ URL `.pages.dev` ฟรีทันที

### 2. สร้าง LIFF App ใน LINE Developers Console
1. เข้าไปที่ [LINE Developers Console](https://developers.line.biz/)
2. เลือก Provider ของ ศอ.10 (หรือสร้างใหม่) -> เข้าไปที่ Channel ประเภท **LINE Login**
3. ไปที่แท็บ **LIFF** -> กดปุ่ม **Add**
   - **LIFF app name:** `Sleep Quest ศอ.10`
   - **Size:** `Full` หรือ `Tall`
   - **Endpoint URL:** ใส่ URL จากข้อ 1 (เช่น `https://nrok47.github.io/sleep-quest/`)
   - **Scopes:** ติ๊ก `profile`, `openid`, `chat_message.write`
   - **Bot link feature:** `Normal`
   - **Share Target Picker:** เปิดเป็น `On` (เพื่อให้แชร์หาเพื่อนได้)
4. จะได้ **LIFF ID** (เช่น `2006123456-ABCdefgh`)

### 3. ใส่ LIFF ID ลงในโค้ด
เปิดไฟล์ `index.html` บรรทัดที่ระบุ config:
```javascript
const LIFF_ID = "ใส่_LIFF_ID_ที่ได้จากข้อ2";
const LINE_OA_URL = "https://line.me/R/ti/p/@ไอดีไลน์คลินิกหลับดี";
```

### 4. แปะปุ่มบน Rich Menu ของ LINE OA
นำ LIFF URL (เช่น `https://liff.line.me/2006123456-ABCdefgh`) ไปใส่ใน Action ของปุ่มบน Rich Menu เช่น:
- ภาพปุ่ม: *"⚔️ ท้าดวลราชาผีอำ (เช็คคุณภาพการนอน)"*
- Action Type: `Open URL` -> ใส่ LIFF URL

---

## 📁 โครงสร้างไฟล์
- `index.html` — ไฟล์เกมตัวเต็ม (HTML5 + CSS3 + Vanilla JS + Web Audio + LIFF SDK v2)
- `README.md` — คู่มือการติดตั้งและเชื่อมต่อ
