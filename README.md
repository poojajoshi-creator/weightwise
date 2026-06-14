# 🌿 WeightWise

A personal weight loss tracker built for a **vegetarian lifestyle**, designed to help you lose 20 lbs over 16 weeks with a sustainable 1.25 lbs/week approach. Log meals, exercise, sleep, vitamins, and weight — all synced across your phone and computer.

---

## ✨ Features

### 📅 Daily Tracking
- **Meal logging** with real calories and protein per food item
- **Exercise logging** — planned workouts + custom exercises with auto calorie calculation using MET values
- **Vitamin & supplement checklist** — daily reminders for Multivitamin, Vitamin D, B12, Joint Multivitamin, Iron, Magnesium
- **Sleep tracker** — log bedtime and wake-up time, auto-calculates hours and quality rating
- **Weight check-in** — daily weight log with progress tracking

### ⭐ The Usual
One-tap shortcut that logs your standard daily meals instantly:
- Breakfast: Oats banana yogurt chia walnut bowl + 3 cups Indian chai
- Lunch: Protein smoothie
- Snacks: Biena edamame ½ cup

### 🔍 Smart Food Search
- **Instant local search** — 60+ pre-loaded foods including Indian dishes, branded snacks, and custom meals
- **Open Food Facts API** — live search of millions of real food products when local results don't match
- **Manual entry** — add any food with custom calories and protein
- **Quantity scaling** — set your portion size and calories/protein scale automatically

### 🍽️ Custom Food Database
Pre-loaded with vegetarian and Indian foods including:
- Indian dishes: Chole, Rajma, Arhar Dal, Chana Dal, Bhindi, Paneer dishes, Roti with ghee
- Branded items: Biena Edamame, Stacy's Pita Chips, Impossible Burger, Panera Bagel, Domino's Pizza
- Restaurant: Topgolf menu items
- Snacks, drinks, smoothies, and more

### 📋 History View
7-day history showing for each day:
- Calories consumed, burned, net calories, and protein
- Exercise completed (shown as tags)
- Weight logged
- Color-coded nutrition stats

### 📈 Progress Tracking
- Weight log with delta from starting weight
- 16-week phase tracker (Foundation → Build Rhythm → Deepen Habits → Finish Strong)
- Progress bar toward 20 lb goal

### 📆 Past Day Logging
Navigate to any previous day using the ← → arrows to backfill missed entries. Yellow banner indicates when viewing a past day.

---

## 🔄 Cross-Device Sync

Data syncs across all your devices via **Supabase** cloud database:
- Sign up with email and password
- Log on your phone → open laptop → same data instantly
- Stays logged in automatically
- Row Level Security ensures only you can access your data

---

## 🏋️ Exercise Calorie Calculation

Custom exercises use **MET (Metabolic Equivalent of Task)** values — a scientifically validated measure of exercise intensity.

```
Calories burned = MET × body weight (kg) × duration (hours)
```

Supports 19 activities including Tai Chi, walking, running, cycling, swimming, yoga, dancing, strength training, and more. Entering distance (miles) for walking/running/cycling refines the MET based on your estimated pace.

---

## 🗺️ 16-Week Plan

| Phase | Weeks | Target |
|-------|-------|--------|
| Foundation | 1–4 | −5 lbs |
| Build Rhythm | 5–8 | −5 lbs |
| Deepen Habits | 9–12 | −5 lbs |
| Finish Strong | 13–16 | −5 lbs |

**Daily calorie target:** 1,400–1,600 cal  
**Daily protein goal:** 70g+  
**Weekly exercise:** 5–6 days  

---

## 🚀 Getting Started

### Prerequisites
- A free [GitHub](https://github.com) account (for hosting)
- A free [Supabase](https://supabase.com) account (for data sync)

### Setup

**1. Clone or download this repository**

**2. Create the Supabase database table**

Go to your Supabase project → SQL Editor and run:

```sql
create table user_data (
  user_id uuid primary key references auth.users(id),
  data jsonb,
  updated_at timestamp default now()
);

alter table user_data enable row level security;

create policy "Users can manage own data" on user_data
  for all using (auth.uid() = user_id);
```

**3. Deploy to GitHub Pages**
- Rename `weightwise.html` to `index.html`
- Push to your GitHub repository
- Go to **Settings → Pages → Deploy from branch (main)**
- Your app will be live at `https://yourusername.github.io/your-repo-name`

**4. Add GitHub Pages URL to Supabase**
- Go to **Supabase → Authentication → URL Configuration**
- Add your GitHub Pages URL to the allowed redirect URLs

**5. Sign up and start tracking**
- Visit your GitHub Pages URL
- Create an account with email and password
- Enter your starting weight
- Start logging!

### Add to Phone Home Screen
On iPhone: tap **Share → Add to Home Screen**  
On Android: tap **Menu → Add to Home Screen**

The app works like a native app icon on your phone.

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Frontend | Plain HTML, CSS, JavaScript (no frameworks) |
| Database | Supabase (PostgreSQL) |
| Auth | Supabase Auth |
| Food API | Open Food Facts (free, open source) |
| Hosting | GitHub Pages |
| Timezone | US Eastern (America/New_York) |

---

## 📱 Usage Tips

- **The Usual button** — use every morning for your standard meals, then add extras on top
- **← → arrows** — navigate to yesterday to log sleep and previous day meals
- **Food search** — type a single keyword like "paneer", "dal", or "smoothie" for best results
- **Quantity scaling** — all food items scale proportionally when you change the quantity
- **Sleep** — log each morning for the previous night using the back arrow

---

## 🔒 Privacy

- All data is private to your account
- Row Level Security in Supabase ensures no one else can access your data
- No ads, no tracking, no third-party analytics
- Open Food Facts API calls are anonymous

---

## 📄 License

Personal use project. Feel free to fork and adapt for your own needs.
